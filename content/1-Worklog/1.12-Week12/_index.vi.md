---
title: "Week 12 Worklog"
date: "`r.Sys.Date()`"
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---

### Mục tiêu Tuần 12:

- Kết nối và làm quen với các thành viên trong First Cloud Journey.
- Nắm được các kiến thức cơ bản về AWS và học cách sử dụng cả giao diện Console và CLI.

### Nhiệm vụ trong tuần:

| Ngày | Nhiệm vụ                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo                                                                                                                      |
| ---- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| 2    | - **Thiết lập AWS Toolkit cho VS Code để sử dụng Amazon Q và CodeWhisperer** <br>&emsp; + Cài đặt tiện ích AWS Toolkit trong Visual Studio Code <br>&emsp; + Kết nối các tài khoản AWS và thiết lập AWS Region cần làm việc <br>&emsp; + Cấu hình phương thức đăng nhập bằng IAM Identity Center, IAM credentials hoặc AWS Builder ID <br>&emsp; + Khám phá và quản lý tài nguyên AWS trực tiếp qua AWS Explorer <br>&emsp; + Sử dụng Amazon Q để giải thích, phân tích lỗi và tối ưu mã nguồn <br>&emsp; + Sử dụng Amazon CodeWhisperer để nhận gợi ý mã theo thời gian thực và quét bảo mật <br> - **Tự động hóa lưu trữ Snapshot EBS bằng Amazon Data Lifecycle Manager** <br>&emsp; + Khởi chạy EC2 để chuẩn bị EBS volumes phục vụ việc sao lưu snapshot <br>&emsp; + Tạo policy Data Lifecycle Manager với một lịch snapshot cơ bản <br>&emsp; + Thiết lập thêm nhiều lịch để xử lý quy trình lưu trữ phức tạp hơn <br>&emsp; + Kiểm tra kết quả chạy policy để xác nhận snapshot được tạo và lưu trữ đúng cách | 11/24/2025   | 11/24/2025      | **AWS Toolkit Configuration:** <https://000087.awsstudygroup.com/> <br> **EBS Snapshot Archiving:** <https://000088.awsstudygroup.com/> |
| 3    | - Tìm hiểu AWS và các nhóm dịch vụ chính <br>&emsp; + Compute <br>&emsp; + Storage <br>&emsp; + Networking <br>&emsp; + Database <br>&emsp; + ... <br>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | 11/25/2025   | 11/25/2025      | <https://cloudjourney.awsstudygroup.com/>                                                                                               |
| 4    | - Tạo tài khoản AWS Free Tier <br> - Tìm hiểu AWS Console & AWS CLI <br> - **Thực hành:** <br>&emsp; + Tạo và cấu hình tài khoản AWS <br>&emsp; + Cài đặt & thiết lập AWS CLI <br>&emsp; + Thực hành các lệnh cơ bản của AWS CLI <br>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | 11/26/2025   | 11/26/2025      | <https://cloudjourney.awsstudygroup.com/>                                                                                               |
| 5    | - Tìm hiểu EC2 cơ bản: <br>&emsp; + Instance types <br>&emsp; + AMI <br>&emsp; + EBS <br>&emsp; + ... <br> - Học cách kết nối SSH vào EC2 <br> - Tìm hiểu Elastic IP <br>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | 11/27/2025   | 11/27/2025      | <https://cloudjourney.awsstudygroup.com/>                                                                                               |
| 6    | - **Thực hành:** <br>&emsp; + Khởi chạy một EC2 instance <br>&emsp; + Kết nối qua SSH <br>&emsp; + Gắn thêm một EBS volume <br>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | 11/28/2025   | 11/28/2025      | <https://cloudjourney.awsstudygroup.com/>                                                                                               |

### Thành tựu Tuần 12:

- Hiểu rõ AWS là gì và nắm được các nhóm dịch vụ chính:

  - Compute
  - Storage
  - Networking
  - Database
  - ...

- Tạo và cấu hình thành công tài khoản AWS Free Tier.

- Sử dụng thành thạo AWS Management Console và biết cách tìm kiếm, truy cập các dịch vụ trên giao diện web.

- Cài đặt và cấu hình AWS CLI bao gồm:

  - Access Key
  - Secret Key
  - Default Region
  - ...

- Sử dụng AWS CLI để thực hiện nhiều thao tác cơ bản như:

  - Kiểm tra thông tin tài khoản & cấu hình
  - Lấy danh sách các vùng (regions)
  - Xem tài nguyên EC2
  - Tạo và quản lý key pairs
  - Theo dõi trạng thái các dịch vụ đang chạy
  - ...

- Có khả năng sử dụng song song cả Console và CLI để quản lý tài nguyên AWS.
- ...
