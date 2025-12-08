---
title: "Week 6 Worklog"
date: "`r Sys.Date()`"
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Mục tiêu tuần 6:

- Học cách quản lý quyền truy cập EC2 bằng IAM với thẻ tài nguyên và permission boundary.
- Thiết lập và cấu hình các công cụ giám sát như Grafana và AWS CloudWatch.
- Sử dụng AWS Systems Manager để tự động vá lỗi và chạy lệnh từ xa.
- Tối ưu hóa EC2 bằng thực hành right-sizing và AWS Compute Optimizer.
- Mã hóa dữ liệu S3 bằng AWS KMS và cấu hình hệ thống ghi nhật ký.
- Phân tích chi phí và mức sử dụng AWS qua Cost Explorer.
- Xây dựng pipeline và data lake bằng S3, Kinesis, Glue, Athena, và QuickSight.
- Tự động hóa triển khai hạ tầng với AWS CloudFormation.

### Nhiệm vụ trong tuần:

| Day | Task                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | Start Date | Completion Date | Reference Material                                                                                                                   |
| --- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| 2   | - **Quản lý quyền truy cập EC2 bằng IAM và thẻ tài nguyên:** <br>&emsp; + Tạo IAM user cho bước chuẩn bị <br>&emsp; + Tạo IAM Policy tùy chỉnh để xác định quyền <br>&emsp; + Tạo IAM Role cho người dùng hoặc dịch vụ assume <br>&emsp; + Kiểm tra chính sách bằng cách chuyển vai trò và kiểm thử quyền <br><br> - **Bắt đầu với Grafana cơ bản:** <br>&emsp; + Tạo VPC và subnet cho môi trường <br>&emsp; + Cấu hình Security Group để kiểm soát traffic <br>&emsp; + Khởi chạy EC2 để cài Grafana <br>&emsp; + Tạo IAM User và Role để truy cập AWS <br>&emsp; + Gán IAM Role cho EC2 instance <br>&emsp; + Cài đặt Grafana trên EC2 <br>&emsp; + Thiết lập dashboard trong Grafana                                                                        | 10/13/2025 | 10/13/2025      | IAM services: <br> <https://000028.awsstudygroup.com/> <br> Grafana basic: <br> <https://000029.awsstudygroup.com/>                  |
| 3   | - **Giới hạn quyền người dùng bằng IAM Permission Boundary:** <br>&emsp; + Thực hiện các bước chuẩn bị <br>&emsp; + Tạo boundary policy định nghĩa quyền tối đa <br>&emsp; + Tạo IAM user mới với quyền hạn chế <br>&emsp; + Kiểm thử mức giới hạn của user <br><br> - **Quản lý bản vá và chạy lệnh từ xa với AWS Systems Manager:** <br>&emsp; + Tạo VPC và subnet <br>&emsp; + Khởi chạy EC2 Windows public <br>&emsp; + Tạo IAM Role phù hợp và gán vào EC2 <br>&emsp; + Cấu hình Patch Manager cho việc vá tự động <br>&emsp; + Sử dụng Run Command để chạy lệnh từ xa                                                                                                                                                                                     | 10/14/2025 | 10/14/2025      | IAM permission boundary: <br> <https://000030.awsstudygroup.com/> <br> AWS Systems Manager: <br> <https://000031.awsstudygroup.com/> |
| 4   | - **Thực hành right-sizing trên EC2:** <br>&emsp; + Tìm hiểu CloudWatch để giám sát <br>&emsp; + Tạo và gán IAM Role cho CloudWatch Agent <br>&emsp; + Cài đặt CloudWatch Agent trên EC2 <br>&emsp; + Sử dụng AWS Compute Optimizer để đề xuất tối ưu EC2 <br><br> - **Mã hóa dữ liệu S3 bằng AWS KMS:** <br>&emsp; + Tạo các IAM roles, groups, users, và policies cần thiết <br>&emsp; + Khởi tạo khóa KMS <br>&emsp; + Tạo S3 bucket và tải dữ liệu lên <br>&emsp; + Thiết lập CloudTrail và Athena để phân tích log <br>&emsp; + Kiểm tra và chia sẻ dữ liệu S3 đã mã hóa                                                                                                                                                                                   | 10/15/2025 | 10/15/2025      | EC2 right-sizing: <br> <https://000032.awsstudygroup.com/> <br> S3 encryption with KMS: <br> <https://000033.awsstudygroup.com/>     |
| 5   | - **Phân tích chi phí AWS bằng Cost Explorer:** <br>&emsp; + Xem dữ liệu chi phí theo dịch vụ và tài khoản <br>&emsp; + Kiểm tra hiệu quả của Savings Plans và Reserved Instances <br>&emsp; + Xem xét độ co giãn chi phí <br>&emsp; + Tạo báo cáo tùy chỉnh cho EC2 <br>&emsp; + Sử dụng Cost Explorer để phân tích chuyên sâu <br>&emsp; + Kiểm tra chi phí truyền dữ liệu <br><br> - **Xây dựng data lake trên AWS:** <br>&emsp; + Tạo IAM Role và Policy cần thiết <br>&emsp; + Tạo S3 bucket để lưu trữ <br>&emsp; + Tạo Kinesis Data Firehose stream cho data ingestion <br>&emsp; + Dùng Glue Crawler để tạo data catalog <br>&emsp; + Thực hiện transform dữ liệu <br>&emsp; + Phân tích dữ liệu qua Athena <br>&emsp; + Tạo dashboard trong QuickSight | 10/16/2025 | 10/17/2025      | AWS Cost Explorer: <br> <https://000034.awsstudygroup.com/> <br> Data lake on AWS: <br> <https://000035.awsstudygroup.com/>          |
| 6   | - **Nghiên cứu AWS CloudWatch để quan sát hệ thống:** <br>&emsp; + Khám phá Metrics và các biểu thức <br>&emsp; + Làm việc với Logs, Logs Insights, và Metric Filters <br>&emsp; + Thiết lập CloudWatch Alarms <br>&emsp; + Tạo CloudWatch Dashboard <br><br> - **Tự động hóa hạ tầng bằng CloudFormation:** <br>&emsp; + Chuẩn bị IAM Users và Roles <br>&emsp; + Tạo template CloudFormation cơ bản <br>&emsp; + Tìm hiểu Custom Resources dùng Lambda <br>&emsp; + Dùng Mappings, StackSets và Drift Detection                                                                                                                                                                                                                                               | 10/17/2025 | 10/17/2025      | AWS CloudWatch: <br> <https://000036.awsstudygroup.com/> <br> AWS CloudFormation: <br> <https://000037.awsstudygroup.com/>           |

### Thành tựu tuần 6:

- Quản lý quyền truy cập EC2 hiệu quả với IAM:

  - Áp dụng tag-based access
  - Thiết lập permission boundary để giới hạn quyền

- Thiết lập hệ thống giám sát đầy đủ:

  - Cài đặt và cấu hình Grafana
  - Sử dụng CloudWatch cho metrics, logs và alarms

- Tận dụng AWS Systems Manager:

  - Tự động hóa cập nhật qua Patch Manager
  - Chạy lệnh từ xa với Run Command

- Cải thiện hiệu suất và chi phí EC2:

  - Cấu hình CloudWatch Agent
  - Tối ưu EC2 bằng Compute Optimizer
  - Phân tích chi phí bằng Cost Explorer

- Bảo mật dữ liệu lưu trữ:

  - Quản lý khóa KMS cho mã hóa S3
  - Sử dụng CloudTrail và Athena để phân tích log

- Xây dựng pipeline data lake hoàn chỉnh:

  - Cấu hình Kinesis và Glue Crawler
  - Truy vấn qua Athena và trực quan hóa bằng QuickSight

- Tự động hóa triển khai bằng CloudFormation:
  - Tạo template triển khai
  - Sử dụng Custom Resources và StackSets khi cần
