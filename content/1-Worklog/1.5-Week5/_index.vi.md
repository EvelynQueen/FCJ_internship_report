---
title: "Week 5 Worklog"
date: "`r Sys.Date()`"
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Mục tiêu Tuần 5:

- Triển khai mạng AWS nâng cao với VPC Peering và Transit Gateway để kết nối nhiều VPC.
- Triển khai ứng dụng full-stack với EC2, RDS, Auto Scaling và CloudFront nhằm tối ưu hóa phân phối.
- Xây dựng cơ chế tự động hóa tiết kiệm chi phí bằng AWS Lambda để quản lý lịch hoạt động của EC2.
- Tạo quy trình CI/CD bằng AWS Developer Tools để tự động hóa triển khai ứng dụng.
- Cấu hình môi trường lưu trữ hybrid bằng AWS Storage Gateway để tích hợp hệ thống on-premises.
- Quản lý hệ thống lưu trữ doanh nghiệp với Amazon FSx và tăng cường bảo mật ứng dụng bằng AWS WAF.
- Sử dụng Tags và Resource Groups để tổ chức và quản trị tài nguyên AWS hiệu quả.
- Nâng cao kỹ năng thao tác bằng AWS Console và CLI.

### Nhiệm vụ trong tuần:

| Ngày | Nhiệm vụ                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo                                                                                                    |
| ---- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | --------------------------------------------------------------------------------------------------------------------- |
| 2    | - **Thiết lập VPC Peering giữa hai VPC:** <br>&emsp; + Khởi tạo CloudFormation Template để dựng môi trường ban đầu <br>&emsp; + Tạo Security Groups để kiểm soát lưu lượng đến EC2 <br>&emsp; + Tạo các EC2 trong mỗi VPC để kiểm tra kết nối <br>&emsp; + Điều chỉnh Network ACLs cho phép lưu lượng giữa các VPC <br>&emsp; + Tạo và chấp nhận kết nối VPC Peering <br>&emsp; + Cập nhật Route Tables để định tuyến giữa các VPC <br>&emsp; + Bật Cross-Peer DNS để phân giải tên giữa các VPC <br><br> - **Triển khai kiến trúc mạng mở rộng với AWS Transit Gateway:** <br>&emsp; + Tạo Key Pair để truy cập an toàn vào EC2 <br>&emsp; + Khởi tạo môi trường bằng CloudFormation Template <br>&emsp; + Tạo Transit Gateway hoạt động như trung tâm mạng <br>&emsp; + Gắn các VPC vào Transit Gateway để liên lạc <br>&emsp; + Cấu hình Route Tables của Transit Gateway để điều hướng lưu lượng <br>&emsp; + Cập nhật Route Tables của VPC để chuyển lưu lượng qua Transit Gateway | 10/06/2025   | 10/06/2025      | VPC Peering: <br> <https://000019.awsstudygroup.com/> <br> Transit Gateway: <br> <https://000020.awsstudygroup.com/>  |
| 3    | - **Triển khai WordPress trên AWS Cloud:** <br>&emsp; + Chuẩn bị VPC và Subnets cho cấu trúc mạng <br>&emsp; + Cài đặt Security Groups cho EC2 và RDS <br>&emsp; + Khởi chạy EC2 để chạy WordPress <br>&emsp; + Triển khai RDS cho cơ sở dữ liệu WordPress <br>&emsp; + Cài đặt và cấu hình WordPress trên EC2 <br>&emsp; + Thiết lập Auto Scaling để bảo đảm tính sẵn sàng <br>&emsp; + Thực hiện backup và restore cơ sở dữ liệu <br>&emsp; + Tích hợp CloudFront tăng tốc và bảo mật <br><br> - **Tối ưu chi phí EC2 bằng Lambda:** <br>&emsp; + Tạo tags để xác định máy EC2 cho tối ưu chi phí <br>&emsp; + Tạo IAM Role cấp quyền cho Lambda <br>&emsp; + Tạo Lambda tự động bật/tắt các EC2 <br>&emsp; + Kiểm thử hoạt động Lambda                                                                                                                                                                                                                                               | 10/07/2025   | 10/07/2025      | WordPress: <br> <https://000021.awsstudygroup.com/> <br> Lambda: <br> <https://000022.awsstudygroup.com/>             |
| 4    | - **Tự động hóa triển khai bằng CI/CD Pipeline:** <br>&emsp; + Chuẩn bị các tài nguyên cần thiết cho pipeline <br>&emsp; + Cài đặt CodeDeploy Agent trên EC2 <br>&emsp; + Tạo CodeCommit repository cho mã nguồn <br>&emsp; + Cấu hình CodeBuild để biên dịch ứng dụng <br>&emsp; + Thiết lập CodeDeploy để tự động triển khai <br>&emsp; + Tạo CodePipeline để điều phối tổng thể quy trình <br>&emsp; + Khắc phục lỗi phát sinh trong pipeline <br><br> - **Sử dụng AWS Storage Gateway cho lưu trữ hybrid:** <br>&emsp; + Tạo S3 Bucket để lưu trữ dữ liệu <br>&emsp; + Dựng EC2 để làm máy chủ Storage Gateway <br>&emsp; + Tạo Storage Gateway kết nối môi trường on-prem với AWS <br>&emsp; + Tạo File Shares để truy cập dạng file <br>&emsp; + Mount File Shares lên máy on-prem để sử dụng                                                                                                                                                                                     | 10/08/2025   | 10/08/2025      | CodePipeline: <br> <https://000023.awsstudygroup.com/> <br> Storage Gateway: <br> <https://000024.awsstudygroup.com/> |
| 5    | - **Quản lý Amazon FSx for Windows File Server:** <br>&emsp; + Tạo môi trường ban đầu <br>&emsp; + Triển khai file system Multi-AZ SSD và HDD <br>&emsp; + Tạo các file share mới <br>&emsp; + Kiểm tra và theo dõi hiệu năng <br>&emsp; + Bật deduplication và shadow copies để tối ưu lưu trữ <br>&emsp; + Quản lý sessions, open files và quotas người dùng <br>&emsp; + Bật Continuous Access để tăng độ sẵn sàng <br>&emsp; + Mở rộng throughput và storage khi cần <br>&emsp; + Xóa môi trường sau khi hoàn tất thử nghiệm <br>&emsp; + Tham khảo AWS CLI để quản lý file server <br><br> - **Cấu hình AWS Web Application Firewall (WAF):** <br>&emsp; + Tạo S3 Bucket và triển khai ứng dụng mẫu <br>&emsp; + Sử dụng AWS WAF với managed rules <br>&emsp; + Tạo custom rules và advanced rules theo nhu cầu <br>&emsp; + Kiểm thử các rule mới <br>&emsp; + Ghi log để phân tích <br>&emsp; + Xóa tất cả tài nguyên để tránh phát sinh chi phí                                 | 10/09/2025   | 10/09/2025      | Amazon FSx: <br> <https://000025.awsstudygroup.com/> <br> AWS WAF: <br> <https://000026.awsstudygroup.com/>           |
| 6    | - **Quản lý tài nguyên AWS bằng Tags và Resource Groups:** <br>&emsp; + Tìm hiểu và sử dụng tags trên AWS Console <br>&emsp; + Khởi chạy EC2 kèm tags <br>&emsp; + Thêm hoặc xóa tags trên tài nguyên có sẵn <br>&emsp; + Lọc tài nguyên bằng tags <br>&emsp; + Sử dụng AWS CLI để quản lý tags <br>&emsp; + Thêm tags cho EC2 có sẵn bằng CLI <br>&emsp; + Gán tags khi tạo tài nguyên bằng CLI <br>&emsp; + Mô tả tài nguyên đã gán tags bằng CLI <br>&emsp; + Tạo và quản lý Resource Group <br>&emsp; + Tạo Resource Group dựa trên tags <br>&emsp; + Xem và quản lý tài nguyên trong nhóm                                                                                                                                                                                                                                                                                                                                                                                          | 10/10/2025   | 10/10/2025      | Tags & Resource Groups: <br> <https://000027.awsstudygroup.com/>                                                      |

### Thành tựu Tuần 5:

- Hoàn thành các cấu hình mạng AWS nâng cao:

  - VPC Peering cho kết nối trực tiếp giữa các VPC
  - Transit Gateway đóng vai trò trung tâm định tuyến
  - Cấu hình DNS và routing giữa các VPC

- Triển khai và tối ưu ứng dụng full-stack trên AWS:

  - WordPress tích hợp RDS
  - Auto Scaling và CloudFront nâng cao hiệu năng
  - Tối ưu chi phí bằng Lambda

- Xây dựng quy trình DevOps tự động:

  - CI/CD đầy đủ với AWS Developer Tools
  - Tự động triển khai bằng CodePipeline
  - Giải pháp lưu trữ hybrid qua Storage Gateway

- Thiết lập hệ thống lưu trữ và bảo mật tầm doanh nghiệp:

  - Amazon FSx Multi-AZ tối ưu hóa hiệu năng
  - AWS WAF với các quy tắc tùy chỉnh
  - Theo dõi và tối ưu lưu trữ

- Áp dụng phương pháp quản trị tài nguyên AWS chuẩn hóa:

  - Chiến lược tagging hỗ trợ quản lý chi phí
  - Resource Groups giúp quản lý tập trung
  - Sử dụng thành thạo AWS Console và CLI

- Tăng cường kỹ năng IaC với CloudFormation để triển khai môi trường nhất quán.
