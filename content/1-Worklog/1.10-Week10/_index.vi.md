---
title: "Week 10 Worklog"
date: "`r Sys.Date()`"
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

### Mục tiêu Tuần 10:

- Triển khai và quản lý ứng dụng bằng Red Hat OpenShift Service on AWS (ROSA) và thiết lập quy trình CI/CD cơ bản.
- Xây dựng và phân tích nền tảng phân tích dữ liệu trên AWS sử dụng streaming ingestion, Glue, EMR, Athena, QuickSight và Redshift.
- Tạo dashboard kinh doanh và theo dõi hoạt động mạng/tài khoản bằng Amazon QuickSight, VPC Flow Logs và phân quyền truy cập billing.
- Phát triển và triển khai ứng dụng đám mây bằng AWS CDK, kiến trúc hướng sự kiện với SNS/SQS và mô hình serverless dựa trên Lambda.
- Xây dựng hệ thống web serverless với API Gateway, Lambda, DynamoDB, Cognito và CloudFront, bao gồm SSL và xác thực.
- Thiết lập xử lý đơn hàng và CI/CD pipeline cho ứng dụng serverless sử dụng SQS, SNS, SAM và CodePipeline.

### Nhiệm vụ trong tuần:

| Day | Công việc                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | Start Date | Completion Date | Tài liệu tham khảo                                                                                                                                                                                                                                                                                       |
| --- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 2   | - **Triển khai Ứng dụng với Red Hat OpenShift Service on AWS (ROSA)** <br>&emsp; + Kích hoạt ROSA và cài đặt CLI cần thiết <br>&emsp; + Tạo và cấu hình cluster OpenShift trên AWS <br>&emsp; + Deploy ứng dụng mẫu lên cluster <br>&emsp; + Thiết lập pipeline CI/CD cơ bản với CodeCommit, CodeBuild và CodePipeline <br>&emsp; + Cấu hình và kiểm tra CI/CD dành riêng cho việc triển khai ứng dụng <br><br> - **Xây dựng Nền tảng Phân tích Dữ liệu trên AWS** <br>&emsp; + Đưa dữ liệu stream vào hệ thống bằng Kinesis Firehose <br>&emsp; + Dùng Glue Crawlers để xây dựng Glue Data Catalog <br>&emsp; + Chuyển đổi dữ liệu bằng Glue Studio, interactive sessions và DataBrew <br>&emsp; + Xử lý dữ liệu lớn với Amazon EMR <br>&emsp; + Phân tích bằng Athena và xử lý thời gian thực bằng Kinesis Data Analytics <br>&emsp; + Tạo dashboard trực quan với QuickSight <br>&emsp; + Cung cấp dữ liệu qua Lambda và xây dựng data warehouse bằng Redshift                | 11/10/2025 | 11/10/2025      | ROSA Hands-on Lab: <br> <https://000071.awsstudygroup.com/> <br> Analytics Platform: <br> <https://000072.awsstudygroup.com/>                                                                                                                                                                            |
| 3   | - **Bắt đầu với Amazon QuickSight** <br>&emsp; + Chuẩn bị dữ liệu và tạo dashboard ban đầu với line chart, pie chart và pivot table <br>&emsp; + Cải tiến dashboard bằng định dạng, thêm visual và bảng dữ liệu chi tiết <br>&emsp; + Tạo dashboard tương tác với filter, filter action và navigation action trước khi xuất bản <br><br> - **Giám sát Hạ tầng Mạng với VPC Flow Logs** <br>&emsp; + Kích hoạt VPC Flow Logs để thu thập dữ liệu IP traffic <br>&emsp; + Gửi log đến CloudWatch Logs <br>&emsp; + Phân tích log để đánh giá security group và lưu lượng mạng <br><br> - **Ủy quyền Truy cập Billing Console** <br>&emsp; + Tạo IAM group và bật quyền truy cập billing <br>&emsp; + Viết IAM policy tùy chỉnh cho quyền billing/cost management <br>&emsp; + Gắn policy vào IAM group để phân quyền <br>&emsp; + Kiểm tra quyền của người dùng trong group                                                                                                        | 11/11/2025 | 11/11/2025      | Amazon QuickSight Guide: <br> <https://000073.awsstudygroup.com/> <br> VPC Flow Logs Lab: <br> <https://000074.awsstudygroup.com/> <br> AWS Billing Console: <br> <https://000075.awsstudygroup.com/>                                                                                                    |
| 4   | - **Phát triển Ứng dụng bằng AWS CDK** <br>&emsp; + Chuẩn bị môi trường bằng IAM Role và EC2 instance <br>&emsp; + Thiết lập VSCode để phát triển <br>&emsp; + Dùng CDK định nghĩa kiến trúc với API Gateway, ELB và ECS <br>&emsp; + Tích hợp Lambda và S3 <br>&emsp; + Tổ chức kiến trúc bằng nested stacks <br><br> - **Xây dựng Kiến trúc Hướng Sự kiện với SNS và SQS** <br>&emsp; + Deploy hạ tầng và cấu hình nguồn sự kiện <br>&emsp; + Tạo mô hình pub/sub với SNS và SQS <br>&emsp; + Áp dụng message filtering cho SNS <br>&emsp; + Sử dụng kỹ thuật lọc nâng cao <br><br> - **Phát triển Ứng dụng Serverless với AWS Lambda** <br>&emsp; + Tạo Lambda xử lý hình ảnh dựa trên sự kiện S3 <br>&emsp; + Tạo S3 bucket và IAM policy cho Lambda <br>&emsp; + Kiểm tra quá trình resize ảnh <br>&emsp; + Tạo DynamoDB table lưu dữ liệu <br>&emsp; + Ghi dữ liệu vào DynamoDB bằng Lambda                                                                                | 11/12/2025 | 11/12/2025      | AWS CDK Development: <br> <https://000076.awsstudygroup.com/> <br> Event-driven Architecture Lab: <br> <https://000077.awsstudygroup.com/> <br> Serverless Lambda Guide: <br> <https://000078.awsstudygroup.com/>                                                                                        |
| 5   | - **Xây dựng Serverless Frontend để Gọi API Gateway** <br>&emsp; + Deploy ứng dụng front-end <br>&emsp; + Tạo DynamoDB table <br>&emsp; + Deploy Lambda để ghi, đọc và xóa dữ liệu <br>&emsp; + Cấu hình API Gateway và bật CORS <br>&emsp; + Kiểm tra API qua Postman và giao diện web <br><br> - **Triển khai Ứng dụng Serverless bằng SAM** <br>&emsp; + Deploy front-end <br>&emsp; + Tạo DynamoDB table <br>&emsp; + Deploy Lambda cho CRUD và resize hình ảnh <br>&emsp; + Thiết lập GET/POST/DELETE cho API Gateway <br>&emsp; + Kiểm thử bằng Postman và giao diện web <br><br> - **Xác thực Serverless với Amazon Cognito** <br>&emsp; + Tạo Cognito User Pool <br>&emsp; + Tạo API và Lambda function <br>&emsp; + Kiểm tra flow xác thực qua front-end <br><br> - **Cấu hình SSL cho ứng dụng serverless** <br>&emsp; + Tạo domain và hosted zone trên Route 53 <br>&emsp; + Yêu cầu SSL certificate qua ACM <br>&emsp; + Tạo CloudFront distribution để hỗ trợ HTTPS | 11/13/2025 | 11/13/2025      | Serverless Frontend with API Gateway: <br> <https://000079.awsstudygroup.com/> <br> Serverless Application with SAM: <br> <https://000080.awsstudygroup.com/> <br> Cognito Authentication Lab: <br> <https://000081.awsstudygroup.com/> <br> SSL Configuration: <br> <https://000082.awsstudygroup.com/> |
| 6   | - **Xử lý Đơn hàng với SQS và SNS** <br>&emsp; + Tạo SQS queue và SNS topic <br>&emsp; + Tạo DynamoDB table cho đơn hàng <br>&emsp; + Phát triển Lambda để checkout, xử lý, quản lý và xóa đơn <br>&emsp; + Kiểm tra toàn bộ quy trình xử lý đơn hàng <br><br> - **Xây dựng CI/CD Pipeline cho Ứng dụng Serverless** <br>&emsp; + Tạo Git repo cho pipeline SAM <br>&emsp; + Cấu hình pipeline SAM qua CodePipeline <br>&emsp; + Tạo Git repo riêng cho front-end <br>&emsp; + Xây dựng pipeline để deploy front-end <br>&emsp; + Kiểm tra hoạt động ứng dụng sau triển khai                                                                                                                                                                                                                                                                                                                                                                                                     | 11/14/2025 | 11/14/2025      | Order Processing with SQS and SNS: <br> <https://000083.awsstudygroup.com/> <br> CI/CD Pipeline for Serverless: <br> <https://000084.awsstudygroup.com/>                                                                                                                                                 |

### Thành tựu Tuần 10:

- Hoàn tất triển khai ứng dụng với ROSA, bao gồm kích hoạt dịch vụ, tạo cluster, deploy ứng dụng mẫu và thiết lập CI/CD bằng CodeCommit, CodeBuild và CodePipeline.

- Xây dựng đầy đủ nền tảng phân tích dữ liệu:

  - Thu thập stream với Kinesis Firehose và lập danh mục dữ liệu qua Glue Crawlers.
  - Chuyển đổi dữ liệu bằng Glue, DataBrew và xử lý trên EMR.
  - Phân tích qua Athena, xử lý thời gian thực qua Kinesis Data Analytics, và hiển thị trên QuickSight.
  - Cung cấp dữ liệu qua Lambda và tổ chức kho dữ liệu bằng Redshift.

- Nâng cao khả năng quan sát và trực quan hóa:

  - Thiết kế dashboard QuickSight tương tác, sử dụng nhiều loại biểu đồ và bộ lọc.
  - Bật và xem xét VPC Flow Logs trong CloudWatch Logs để hiểu hành vi mạng.
  - Phân quyền truy cập billing console thông qua IAM group và custom policy.

- Phát triển hạ tầng và ứng dụng dựa trên AWS CDK và kiến trúc hướng sự kiện:

  - Thiết lập môi trường CDK trên EC2 và IAM.
  - Xây dựng kiến trúc tích hợp API Gateway, ELB, ECS, Lambda và S3.
  - Tạo luồng xử lý sự kiện SNS–SQS với message filtering nâng cao.
  - Xây dựng workflow xử lý hình ảnh và lưu dữ liệu qua Lambda và DynamoDB.

- Xây dựng hệ thống serverless hoàn chỉnh:

  - Deploy front-end kết nối API Gateway + Lambda + DynamoDB bằng thủ công và SAM.
  - Tích hợp Cognito để xác thực và kiểm tra quy trình qua front-end và Postman.
  - Bảo mật ứng dụng bằng domain riêng, Route 53, ACM certificate và CloudFront.

- Triển khai xử lý đơn hàng và tự động hóa CI/CD:
  - Xây dựng hệ thống xử lý đơn hàng dựa trên SQS/SNS, DynamoDB và Lambda.
  - Thiết lập CI/CD cho backend SAM và front-end qua CodePipeline và Git repositories.
