---
title: "Week 4 Worklog"
date: "'r.Sys.Date() '"
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu Tuần 4 :

- Nắm cách cấu hình Amazon RDS, bao gồm thiết lập VPC, nhóm bảo mật và thao tác sao lưu/khôi phục.
- Tìm hiểu triển khai ứng dụng mở rộng bằng Auto Scaling Groups và Application Load Balancers.
- Hiểu các phương pháp giám sát thông qua CloudWatch (metrics, logs, alarms, dashboards).
- Khám phá kiến trúc DNS lai dành cho doanh nghiệp bằng Route 53 Resolver.
- Củng cố kỹ năng AWS CLI để tự động hóa thao tác trên S3, EC2, IAM và VPC.
- Xây dựng pipeline CI/CD bằng CodeCommit, CodeBuild, CodeDeploy và CodePipeline.
- Thực hành tự động hóa sao lưu bằng AWS Backup cùng chính sách vòng đời.
- Triển khai ứng dụng container bằng Docker và sử dụng registry trên AWS.
- Nghiên cứu quy trình di chuyển máy ảo với VM import/export giữa on-prem và AWS.
- Xây dựng ứng dụng serverless bằng AWS Lambda và API Gateway cùng cấu hình IAM.
- Tìm hiểu giám sát bảo mật thông qua AWS Security Hub với tích hợp đa dịch vụ.

### Công việc trong tuần:

| Ngày | Nhiệm vụ                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo                                                                                                                                                                       |
| ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 2    | - **Quản lý CSDL quan hệ với Amazon RDS:** <br>&emsp; + Tạo VPC, cấu hình security group cho EC2 và RDS, thiết lập DB subnet group. <br>&emsp; + Khởi tạo EC2 và RDS instance. <br>&emsp; + Deploy ứng dụng mẫu trên EC2 và kết nối tới RDS. <br>&emsp; + Thực hiện sao lưu và khôi phục. <br>&emsp; + Xóa toàn bộ tài nguyên sau khi hoàn tất. <br><br> - **Triển khai ứng dụng mở rộng với Auto Scaling:** <br>&emsp; + Xây dựng hạ tầng mạng (VPC, subnets, security groups). <br>&emsp; + Tạo EC2 Launch Template. <br>&emsp; + Thiết lập Target Group và ALB. <br>&emsp; + Tạo Auto Scaling Group với nhiều policy khác nhau. <br>&emsp; + Dọn dẹp tài nguyên AWS sau khi thử nghiệm. <br><br> - **Giám sát tài nguyên bằng CloudWatch:** <br>&emsp; + Xem và phân tích metrics bằng search & math expressions. <br>&emsp; + Truy vấn log bằng CloudWatch Logs Insights. <br>&emsp; + Tạo Metric Filter để trích dữ liệu. <br>&emsp; + Tạo CloudWatch Alarm với ngưỡng cảnh báo. <br>&emsp; + Tạo custom dashboard để theo dõi. <br>&emsp; + Xóa tất cả tài nguyên sau khi hoàn thành. | 29/09/2025   | 29/09/2025      | Amazon RDS: <br> <https://000005.awsstudygroup.com/> <br> Auto Scaling Group: <br> <https://000006.awsstudygroup.com/> <br> CloudWatch Metrics: <br> <https://000008.awsstudygroup.com/> |
| 3    | - **Triển khai DNS lai với Route 53 Resolver:** <br>&emsp; + Khởi tạo hạ tầng qua CloudFormation. <br>&emsp; + Cài đặt Microsoft Active Directory làm máy chủ DNS nội bộ mô phỏng. <br>&emsp; + Tạo outbound endpoint để chuyển tiếp truy vấn DNS từ VPC. <br>&emsp; + Cấu hình rule để định tuyến truy vấn DNS chính xác. <br>&emsp; + Thiết lập inbound endpoint cho môi trường on-prem truy cập VPC. <br>&emsp; + Kiểm tra phân giải DNS hai chiều và cleanup tài nguyên. <br><br> - **Quản lý AWS bằng CLI:** <br>&emsp; + Cài đặt và cấu hình AWS CLI với credentials và region. <br>&emsp; + Sử dụng CLI để xem và mô tả tài nguyên S3, SNS, IAM. <br>&emsp; + Thực hiện thao tác bucket và object trong S3 thông qua CLI. <br>&emsp; + Tạo các thành phần VPC (như Internet Gateway) bằng CLI. <br>&emsp; + Khởi tạo, mô tả và xóa EC2 instance hoàn toàn bằng CLI. <br>&emsp; + Cleanup toàn bộ tài nguyên đã tạo.                                                                                                                                                                  | 30/09/2025   | 30/09/2025      | Route 53 Resolver: <br> <https://cloudjourney.awsstudygroup.com/> <br> AWS CLI: <br> <https://000011.awsstudygroup.com/>                                                                 |
| 4    | - **Xây dựng pipeline CI/CD:** <br>&emsp; + Tạo repository CodeCommit cho source code. <br>&emsp; + Cấu hình CodeBuild để build, test, package ứng dụng. <br>&emsp; + Tạo cấu hình CodeDeploy và deployment group. <br>&emsp; + Dựng pipeline tự động bằng CodePipeline. <br>&emsp; + Kiểm thử bằng cách đẩy code mới và quan sát tự động deploy. <br>&emsp; + Dọn dẹp toàn bộ tài nguyên sau khi kết thúc. <br><br> - **Tự động backup EC2 bằng AWS Backup:** <br>&emsp; + Tạo hạ tầng qua CloudFormation. <br>&emsp; + Tạo backup plan với policy vòng đời. <br>&emsp; + Bật thông báo trạng thái backup. <br>&emsp; + Kiểm thử backup/restore. <br>&emsp; + Xóa toàn bộ tài nguyên và bản sao lưu.                                                                                                                                                                                                                                                                                                                                                                                       | 01/10/2025   | 01/10/2025      | AWS IAM Identity Center: <br> <https://000012.awsstudygroup.com/> <br> AWS Backup: <br> <https://000013.awsstudygroup.com/>                                                              |
| 5    | - **Triển khai ứng dụng Docker trên AWS:** <br>&emsp; + Thiết lập VPC, IAM, và các tài nguyên cần thiết. <br>&emsp; + Khởi tạo RDS cho dữ liệu ứng dụng. <br>&emsp; + Cài đặt EC2 cùng các phụ thuộc chạy Docker. <br>&emsp; + Deploy ứng dụng bằng Docker image. <br>&emsp; + Redeploy bằng Docker Compose cho môi trường nhiều container. <br>&emsp; + Push image lên ECR hoặc Docker Hub. <br>&emsp; + Cleanup hạ tầng. <br><br> - **Di chuyển máy ảo lên/xuống AWS:** <br>&emsp; + Xuất VM từ on-prem. <br>&emsp; + Upload bản xuất lên S3. <br>&emsp; + Import vào AWS thành AMI mới. <br>&emsp; + Khởi tạo EC2 từ AMI đã import. <br>&emsp; + Xuất EC2 VM về S3. <br>&emsp; + Xóa tất cả tài nguyên liên quan.                                                                                                                                                                                                                                                                                                                                                                        | 02/10/2025   | 02/10/2025      | Docker on AWS: <br> <https://000015.awsstudygroup.com/> <br> VM Import/Export: <br> <https://000014.awsstudygroup.com/>                                                                  |
| 6    | - **Triển khai ứng dụng serverless (Lambda + API Gateway):** <br>&emsp; + Chuẩn bị gói deploy Lambda cùng dependencies. <br>&emsp; + Tạo IAM role dành cho Lambda. <br>&emsp; + Tạo Lambda function và cấu hình runtime. <br>&emsp; + Tạo API Gateway HTTP API và tích hợp Lambda. <br>&emsp; + Deploy API và kiểm thử qua URL công khai. <br>&emsp; + Xóa toàn bộ tài nguyên Lambda và API. <br><br> - **Giám sát bảo mật với AWS Security Hub:** <br>&emsp; + Bật Security Hub để tập hợp dữ liệu bảo mật đa dịch vụ. <br>&emsp; + Xem dashboard tổng hợp cảnh báo. <br>&emsp; + Sắp xếp ưu tiên cảnh báo từ GuardDuty, Inspector, Macie. <br>&emsp; + Phân tích rủi ro thông qua biểu đồ và bảng tổng hợp.                                                                                                                                                                                                                                                                                                                                                                               | 03/10/2025   | 03/10/2025      | AWS Lambda: <br> <https://000016.awsstudygroup.com/> <br> AWS Security Hub: <br> <https://000018.awsstudygroup.com/>                                                                     |

### Thành tự tuần 4:

- Hoàn thiện cấu hình và quản lý Amazon RDS:

  - Thiết lập VPC và security groups
  - Tạo DB subnet group và kết nối EC2-RDS
  - Deploy ứng dụng kết nối cơ sở dữ liệu
  - Thực hiện sao lưu và phục hồi

- Triển khai hệ thống mở rộng bằng Auto Scaling:

  - Thiết lập mạng (VPC, subnets, SGs)
  - Cấu hình Launch Template
  - ALB + Target Group điều phối traffic
  - Auto Scaling Group với nhiều policy

- Thiết lập hệ thống giám sát với CloudWatch:

  - Phân tích metrics nâng cao
  - Truy vấn log bằng Logs Insights
  - Tạo alarm theo ngưỡng
  - Thiết kế dashboard riêng

- Xây dựng DNS lai bằng Route 53 Resolver:

  - Deploy môi trường bằng CloudFormation
  - Tích hợp Active Directory
  - Endpoint outbound/inbound
  - Kiểm thử phân giải DNS hai chiều

- Nâng cao kỹ năng tự động hóa bằng AWS CLI:

  - Cấu hình CLI
  - Quản lý tài nguyên S3, SNS, IAM
  - Thao tác bucket/object
  - Quản lý vòng đời EC2 từ CLI

- Xây dựng CI/CD pipeline:

  - Tạo repo CodeCommit
  - Thiết lập build với CodeBuild
  - Tự động deploy bằng CodeDeploy
  - Điều phối toàn bộ pipeline bằng CodePipeline

- Ứng dụng chiến lược backup tự động bằng AWS Backup:

  - Deploy hạ tầng CloudFormation
  - Tạo backup plan có lifecycle
  - Cấu hình thông báo
  - Kiểm thử phục hồi dữ liệu

- Deploy ứng dụng container bằng Docker:

  - Thiết lập AWS infrastructure
  - Tích hợp RDS
  - Deploy Docker và Docker Compose
  - Push image lên ECR

- Thực hiện quy trình di chuyển máy ảo:

  - Xuất VM on-prem
  - Chuyển image qua S3
  - Import thành AMI
  - Khởi tạo EC2 từ AMI

- Xây dựng ứng dụng serverless:

  - Chuẩn bị package Lambda
  - Tạo IAM role
  - Tạo Lambda + API Gateway
  - Kiểm thử toàn bộ luồng

- Kích hoạt giám sát bảo mật tập trung với Security Hub:
  - Tập hợp dữ liệu cảnh báo đa dịch vụ
  - Quan sát dashboard
  - Sắp xếp phát hiện từ GuardDuty, Inspector, Macie
  - Phân tích rủi ro tổng hợp
