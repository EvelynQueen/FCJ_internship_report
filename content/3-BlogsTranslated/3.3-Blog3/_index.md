---
title: "Simplify log rotation with Amazon S3 Express One Zone"
date: "2025-08-14"
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---

## AWS Storage Blog

# Simplify log rotation with Amazon S3 Express One Zone

> Author : by Arushi Garg and Matthew Russo on 14 AUG 2025 in Advanced (300)  
> Categories : Amazon Simple Storage Service (S3), Storage, Technical How-to Permalink Comments Share

---

Log rotation is a standard operational practice for maintaining system health and performance while managing storage costs effectively.

**Key points:**

- Involves systematically archiving log files.
- Prevents log files from consuming excessive storage.
- When a log file reaches a certain size or age, it’s rotated:
  - Current file archived with a new name.
  - Fresh log file is created to continue recording events.

Amazon S3 Express One Zone is a high-performance, single-Availability Zone storage class:

- Purpose-built for frequently accessed data and latency-sensitive applications.
- 2024: added support to **append data directly to existing objects**.
- 2025: added **RenameObject API** to rename objects atomically.

---

## Solution overview

- Configure **Log4j2** to write logs directly to a directory bucket in S3 Express One Zone.
- Use **Mountpoint** to mount the directory bucket as a local filesystem.
- Mountpoint version **1.19.0 or later** is required for renaming files.
- Logs are appended via Mountpoint, and file renames are translated into **RenameObject API calls**.

---

## Solution walkthrough

**Steps to implement:**

1. Create required AWS resources (directory bucket, IAM role, EC2 instance).
2. Prepare workspace (install Mountpoint, Maven).
3. Write Java application using Log4j2.
4. Run application and monitor logs.

---

### Step 1: Create the required AWS resources

1. Create a directory bucket:

   - Example: `logging-on-express--usw2-az3--x-s3`.

2. Create an IAM role for EC2:

   - Role name: `logging-on-express`
   - Trusted entity: AWS service → EC2

3. Add an **inline policy** to allow S3 Express One Zone to make `CreateSession` API calls:

   - Policy name: `express-create-session`

4. Launch an EC2 instance:
   - AMI: Amazon Linux 2023
   - Instance type: `t3.micro`
   - Storage: 24 GiB gp3 EBS
   - Subnet in same AZ as bucket
   - Assign IAM role `logging-on-express`

---

### Step 2: Prepare your workspace

1. Connect to EC2 instance.
2. Install dependencies: **Mountpoint** and **Maven**.
3. Verify Mountpoint version:

```bash
$ mount-s3 --version
mount-s3 1.19.0
```

````

4. Create directories:

```bash
$ cd $HOME
$ mkdir logging-on-express
$ cd logging-on-express/
$ mkdir logs
$ pwd
/home/ssm-user/logging-on-express
```

5. Mount directory bucket using `/etc/fstab`:

```bash
$ export MNT_PATH="$HOME/logging-on-express/logs"
$ export BUCKET_NAME="logging-on-express--usw2-az3--x-s3"
$ echo "s3://$BUCKET_NAME $MNT_PATH mount-s3 _netdev,nosuid,nodev,rw,incremental-upload,write-part-size=8388608,allow-other,uid=$(id -u $(whoami)),gid=$(id -g $(whoami)) 0 0" | sudo tee -a /etc/fstab
```

6. Reload system and mount:

```bash
$ sudo systemctl daemon-reload
$ sudo systemctl restart "$(systemd-escape --suffix=mount --path $MNT_PATH)"
$ sudo systemctl status "$(systemd-escape --suffix=mount --path $MNT_PATH)"
$ sudo df -h
```

---

### Step 3: Write a Java application for logging

1. Create **pom.xml** for Log4j2 dependency.
2. Configure Log4j2 (`src/main/resources/log4j2.xml`):

- Directory: `$HOME/logs`
- Rotation: every 1 minute or 10 GB
- File pattern: `${LOG_DIR}/app-%d{yyyy-MM-dd-HH-mm}-%i.log`

3. Sample Java program `LoggingApp.java`:

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

---

### Step 4: Run the application and monitor the logs

1. Build application:

```bash
$ mvn clean package
```

2. Run application:

```bash
$ java -jar target/logging-on-express-1.0-SNAPSHOT-jar-with-dependencies.jar
```

**Observations:**

- Logs append to `app.log`.
- Every minute or 10 GB, `app.log` is renamed.
- Mountpoint translates actions to **S3 `PutObject`** and **`RenameObject` API** calls.

---

### Clean up

- Terminate EC2 instance.
- Delete S3 directory bucket.

---

### Conclusion

- Built log rotation solution using S3 Express One Zone.
- Log4j2 + Mountpoint allows direct logging to S3.
- Rotate logs without requiring local storage.

---

**TAGS:** Amazon S3 Express One Zone, Amazon Simple Storage Service (Amazon S3), AWS Cloud Storage

**Authors:**

- **Arushi Garg**: Product Manager, Amazon S3. Loves singing with ukulele and travel.
- **Matthew Russo**: Senior Software Development Engineer, AWS S3 Express One Zone team.
````
