---
title: "AWS Storage Blog"
date: "2025-08-14"
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---

## Simplify log rotation with Amazon S3 Express One Zone

**Tác giả:** Arushi Garg và Matthew Russo  
**Ngày đăng:** 14/08/2025  
**Chuyên mục:** Advanced (300), Amazon Simple Storage Service (S3), Storage, Technical How-to

---

Log rotation là một thực tiễn vận hành tiêu chuẩn để duy trì system health và hiệu năng, đồng thời quản lý storage costs hiệu quả. Thực tiễn này bao gồm việc lưu trữ có hệ thống các log files để ngăn chúng chiếm dụng quá nhiều storage. Khi một log file đạt đến một dung lượng hoặc độ tuổi nhất định, nó sẽ được rotated — nghĩa là file hiện tại được lưu trữ với một tên mới và một log file mới được tạo để tiếp tục ghi lại các sự kiện mới. Quy trình này giúp duy trì hiệu năng hệ thống yêu cầu và tận dụng storage hiệu quả, đồng thời làm cho log data dễ quản lý và phân tích hơn. Vì các applications liên tục tạo ra log data, các tổ chức cần những storage solutions có khả năng xử lý frequent writes và updates vào log data với hiệu năng cao ổn định, đồng thời tối ưu hóa chi phí lưu trữ.

Amazon S3 Express One Zone là một high-performance, single-Availability Zone storage class được xây dựng đặc biệt cho most frequently accessed data và các latency-sensitive applications. Vào năm 2024, S3 Express One Zone đã bổ sung tính năng append data trực tiếp vào existing objects. Với tính năng này, bạn có thể append data directly to existing objects mà không cần phải download đối tượng, nối dữ liệu mới cục bộ rồi upload lại toàn bộ đối tượng. Điều này cho phép bạn cấu hình applications để ghi log trực tiếp vào S3 Express One Zone mà không cần local storage.

Vào tháng 6/2025, S3 Express One Zone cũng bổ sung hỗ trợ renaming objects với RenameObject API mới. Lần đầu tiên trong Amazon S3, bạn có thể rename các existing objects một cách atomic (chỉ với một thao tác duy nhất) mà không cần di chuyển dữ liệu. API mới này đặc biệt hữu ích cho log rotation vì giờ đây bạn có thể atomically rename các log files của mình trong S3 Express One Zone thay vì phải rename cục bộ, upload lại file đã đổi tên rồi delete file gốc.

Trong blog post này, chúng tôi sẽ minh họa một chiến lược log rotation sử dụng S3 Express One Zone. Chúng tôi sẽ đề cập đến việc sử dụng chức năng append để ghi thêm log entries mới vào cuối các log files hiện có, cũng như sử dụng RenameObject API để atomically rename log file của bạn cho mục đích rotation. Ngoài ra, chúng tôi cũng chỉ cho bạn cách sử dụng Mountpoint for Amazon S3 để mount S3 directory bucket trong S3 Express One Zone storage class như một local filesystem. Mountpoint giúp các applications sử dụng standard logging framework như Log4j2 dễ dàng tận dụng những khả năng mới này trong S3 Express One Zone.

---

## Solution overview

Trong giải pháp này, bạn cấu hình Log4j2, một logging framework phổ biến cho ngôn ngữ lập trình Java, để ghi logs trực tiếp vào một directory bucket trong S3 Express One Zone storage class. Bạn sẽ sử dụng Mountpoint để mount directory bucket như một local filesystem. Lưu ý rằng bạn cần Mountpoint version 1.19.0 hoặc mới hơn để có thể rename files bằng Mountpoint.

Khi Log4j2 ghi thêm (append) các log entries vào filesystem, bạn sẽ thấy rằng Mountpoint gửi append requests đến S3 Express One Zone. Bạn cũng sẽ cấu hình Log4j2 để rotate log files dựa trên một specific time period hoặc một size limit. Khi các log files này được rotated, bạn sẽ thấy Mountpoint dịch các thao tác rename log files thành RenameObject API calls đến S3 Express One Zone.

---

## Solution walkthrough

Để triển khai một logging solution với S3 Express One Zone, bạn cần thực hiện bốn bước:

1. Tạo các AWS resources cần thiết, chẳng hạn như directory bucket, IAM role, và một EC2 instance.
2. Chuẩn bị môi trường làm việc bằng cách tải về các dependencies như Mountpoint và Maven, công cụ dùng để build và chạy một Java application.
3. Viết một Java application sử dụng Log4j2 để ghi logs và rotate log files.
4. Chạy application và giám sát logs.

### Bước 1: Tạo các tài nguyên AWS cần thiết

- Tạo một directory bucket. Ví dụ: `logging-on-express--usw2-az3--x-s3`.
- Tạo IAM role cho EC2 instance:
  - Trusted entity: AWS service → EC2
  - IAM role name: `logging-on-express`
- Tạo inline policy để cho phép S3 Express One Zone thực hiện API `CreateSession`:
  - Policy name: `express-create-session`
- Khởi chạy EC2 instance:
  - AMI: Amazon Linux 2023
  - Instance type: `t3.micro`
  - Storage: 24 GiB gp3 EBS
  - Subnet trong cùng AZ với bucket
  - IAM instance profile: `logging-on-express`

### Bước 2: Chuẩn bị workspace

- Kết nối EC2 instance, cài Mountpoint và Maven.
- Kiểm tra Mountpoint version:

```bash
$ mount-s3 --version
mount-s3 1.19.0
```


- Tạo thư mục logging:

```bash
$ cd $HOME
$ mkdir logging-on-express
$ cd logging-on-express/
$ mkdir logs
```

- Mount directory bucket bằng `/etc/fstab`:

```bash
$ export MNT_PATH="$HOME/logging-on-express/logs"
$ export BUCKET_NAME="logging-on-express--usw2-az3--x-s3"
$ echo "s3://$BUCKET_NAME $MNT_PATH mount-s3 _netdev,nosuid,nodev,rw,incremental-upload,write-part-size=8388608,allow-other,uid=$(id -u $(whoami)),gid=$(id -g $(whoami)) 0 0" | sudo tee -a /etc/fstab
$ sudo systemctl daemon-reload
$ sudo systemctl restart "$(systemd-escape --suffix=mount --path $MNT_PATH)"
$ sudo systemctl status "$(systemd-escape --suffix=mount --path $MNT_PATH)"
$ sudo df -h
```

### Bước 3: Viết ứng dụng Java để logging

- Tạo `pom.xml` với dependency Log4j2.
- Cấu hình `log4j2.xml`:

```xml
<Configuration status="WARN">
    <Properties>
        <Property name="LOG_DIR">logs</Property>
        <Property name="MAX_FILE_SIZE">10GB</Property>
        <Property name="FILE_PATTERN">${LOG_DIR}/app-%d{yyyy-MM-dd-HH-mm}-%i.log</Property>
    </Properties>
    <Appenders>
        <Console name="Console" target="SYSTEM_OUT">
            <PatternLayout pattern="%d{HH:mm:ss.SSS} [%t] %-5level %logger{36} - %msg%n"/>
        </Console>
        <RollingFile name="RollingFile"
                     fileName="${LOG_DIR}/app.log"
                     filePattern="${FILE_PATTERN}">
            <PatternLayout pattern="%d{HH:mm:ss.SSS} [%t] %-5level %logger{36} - %msg%n"/>
            <Policies>
                <TimeBasedTriggeringPolicy interval="1" modulate="true"/>
                <SizeBasedTriggeringPolicy size="${MAX_FILE_SIZE}"/>
            </Policies>
            <DefaultRolloverStrategy fileIndex="nomax"/>
        </RollingFile>
    </Appenders>
    <Loggers>
        <Root level="info">
            <AppenderRef ref="RollingFile"/>
        </Root>
    </Loggers>
</Configuration>
```

- Chương trình Java `LoggingApp.java`:

```java
package com.example;
import org.apache.logging.log4j.LogManager;
import org.apache.logging.log4j.Logger;
import java.util.concurrent.*;
import java.util.concurrent.atomic.AtomicLong;

public class LoggingApp {
    private static final Logger logger = LogManager.getLogger(LoggingApp.class);
    private static final int NUM_THREADS = 50;
    private static final int LOG_INTERVAL_MS = 1;
    private static final AtomicLong counter = new AtomicLong(0);
    private static final ExecutorService executor = Executors.newFixedThreadPool(NUM_THREADS);

    public static void main(String[] args) {
        Runtime.getRuntime().addShutdownHook(new Thread(() -> {
            executor.shutdown();
            try {
                if (!executor.awaitTermination(5, TimeUnit.SECONDS)) executor.shutdownNow();
            } catch (InterruptedException e) { executor.shutdownNow(); }
        }));

        for (int i = 0; i < NUM_THREADS; i++) {
            final int threadId = i;
            executor.submit(() -> {
                while (!Thread.currentThread().isInterrupted()) {
                    long count = counter.incrementAndGet();
                    logger.info("Thread {} - Log #{}", threadId, count);
                    Thread.sleep(LOG_INTERVAL_MS);
                }
                return null;
            });
        }

        while (true) {}
    }
}
```

### Bước 4: Chạy ứng dụng và giám sát logs

```bash
$ mvn clean package
$ java -jar target/logging-on-express-1.0-SNAPSHOT-jar-with-dependencies.jar
```

- Logs sẽ được ghi vào `app.log`.
- Mỗi phút hoặc sau 10GB, file log sẽ được rename atomic bằng `RenameObject API`.
- Quan sát data events trong CloudTrail để xem các request `PutObject` và `RenameObject`.

---

## Clean up

- Terminate EC2 instance.
- Xóa S3 directory bucket.

---

## Conclusion

- Bạn đã học cách xây dựng giải pháp xoay vòng log sử dụng S3 Express One Zone.
- Sử dụng Log4j2 + Mountpoint cho phép ghi log trực tiếp lên S3 mà không cần local storage.
- Có thể mở rộng cho các công cụ logging khác.

---

### TAGS

Amazon S3 Express One Zone, Amazon Simple Storage Service (Amazon S3), AWS Cloud Storage

---

### Authors

**Arushi Garg**
Product Manager tại Amazon S3. Cô thích tìm hiểu các vấn đề của khách hàng và sáng tạo giải pháp để giải quyết chúng. Ngoài công việc, cô thích hát khi chơi ukulele và luôn tìm kiếm cơ hội du lịch.

**Matthew Russo**
Senior Software Development Engineer tại AWS, làm việc trong nhóm S3 Express One Zone.



