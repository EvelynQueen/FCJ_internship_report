---
title: "Week 2 Worklog"
date: "`r Sys.Date()`"
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Mục tiêu tuần 2:

- Làm rõ và xác định phạm vi cho dự án game đánh máy đầu tiên (tính năng cốt lõi, ranh giới microservice, định hướng hệ thống matchmaking trong tương lai).
- Thiết lập nền tảng làm việc nhóm: kho mã dùng chung, backlog ban đầu, mô hình ER, lựa chọn công nghệ và phân công sở hữu microservice.
- Hoàn thiện công thức tiêu chuẩn cho WPM và độ chính xác.
- Xây dựng bản prototype FastAPI gồm sinh văn bản, ghép câu, và chat; đồng thời xác định lộ trình tích hợp Bedrock.
- Cấu hình AWS Budgets kèm cảnh báo chi phí.
- Nâng cao kỹ năng về: Lambda (function URL), mạng VPC (subnet, gateway, kết nối), Flow Logs và các khái niệm về load balancing.
- Khởi tạo Amazon RDS; thiết kế schema và đưa vào dữ liệu ban đầu liên quan đến nội dung text.
- Chuyển đổi TextService để truy xuất từ cơ sở dữ liệu; đo tốc độ so với phương pháp dùng API trước đây.
- Bắt đầu áp dụng các quy trình vận hành sớm: vai trò rõ ràng, thói quen benchmark và định hướng mở rộng.

### Công việc thực hiện trong tuần:

| Day | Task                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | Start Date | Completion Date | Reference Material                                                                                                                                                                                                                                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 2   | - Tổ chức buổi thảo luận nhóm nhằm xác định và ưu tiên các ý tưởng tính năng cho dự án chính <br>&emsp; + Chuyển toàn bộ ghi chú brainstorming từ project canvas sang backlog có cấu trúc <br>&emsp; + Tra cứu và ghi lại công thức WPM và độ chính xác để đồng bộ cách tính <br>&emsp; + Tạo kho mã dùng chung và thiết lập cấu trúc thư mục cho từng microservice và ngôn ngữ sử dụng <br>&emsp; + Điều chỉnh bản phác ER và bắt đầu thiết kế schema cơ sở dữ liệu ban đầu <br>&emsp; + Phân công rõ ràng người phụ trách từng microservice <br>                                                                                                                                                                             | 09/15/2025 | 09/15/2025      |                                                                                                                                                                                                                                                               |
| 3   | - Thiết lập AWS Budgets: <br>&emsp; + Xem lại các loại budget (Cost, Usage, RI, v.v.) <br>&emsp; + Đặt ngưỡng chi phí hàng tháng <br>&emsp; + Tạo budget trong AWS Console <br>&emsp; + Cấu hình cảnh báo qua SNS/email <br/> - Tạo ứng dụng web nhỏ bằng AWS Lambda: <br>&emsp; + Nắm các khái niệm cơ bản của Lambda và function URL <br>&emsp; + Viết hàm “Hello World” đơn giản <br>&emsp; + Cấu hình IAM cần thiết <br>&emsp; + Kích hoạt và kiểm thử function URL endpoint <br/> - Tìm hiểu FastAPI: <br>&emsp; + Làm theo hướng dẫn chính thức của FastAPI <br>&emsp; + Thiết lập môi trường phát triển cục bộ <br>&emsp; + Xây dựng bản thử nghiệm API <br>&emsp; + Tạo các endpoint cơ bản và kiểm tra qua Swagger UI | 09/16/2025 | 09/16/2025      | AWS Lambda:<br/> <https://ap-southeast-1.console.aws.amazon.com/lambda> <br/> AWS Budgets:<br/> <https://us-east-1.console.aws.amazon.com/costmanagement/> <br/> FastAPI:<br/> <https://www.coursera.org/learn/packt-mastering-rest-apis-with-fastapi-1xeea/> |
| 4   | - Khám phá nền tảng mạng và bảo mật AWS <br>&emsp; + Hiểu Amazon VPC và vai trò của môi trường cô lập <br>&emsp; + Phân biệt public subnet và private subnet <br>&emsp; + Tìm hiểu chức năng Internet Gateway và NAT Gateway <br>&emsp; + Sử dụng VPC Flow Logs để theo dõi lưu lượng mạng <br>&emsp; + So sánh phương án kết nối: Site-to-Site VPN và Direct Connect <br>&emsp; + Hiểu khi nào dùng VPC Peering và khi nào dùng Transit Gateway <br>&emsp; + Xem tổng quan về Elastic Load Balancing trong việc phân phối lưu lượng <br>                                                                                                                                                                                      | 09/17/2025 | 09/17/2025      | Module 02-(01 to 03): <br> <https://www.youtube.com/watch?v=O9Ac_vGHquM> <br> <https://www.youtube.com/watch?v=BPuD1l2hEQ4> <br> <https://www.youtube.com/watch?v=CXU8D3kyxIc>                                                                                |
| 5   | - Trải nghiệm Amazon Bedrock playground: <br>&emsp; + Xem các mô hình nền tảng có sẵn (Claude, Titan, v.v.) <br>&emsp; + Chọn mô hình phục vụ sinh văn bản <br>&emsp; + Thử nhiều prompt và điều chỉnh tham số <br>&emsp; + Tạo và đánh giá kết quả mẫu <br/> - Phát triển prototype microservice được giao: <br>&emsp; + Xây dựng logic xử lý và tích hợp nhiều API sinh văn bản <br>&emsp; + Tạo chức năng tạo câu ngẫu nhiên và chat <br>&emsp; + Rà soát phiên bản đầu để nhận diện hạn chế và bước cải thiện tiếp theo <br>&emsp; + Xác nhận tính khả thi của hướng triển khai kỹ thuật <br>                                                                                                                              | 09/18/2025 | 09/18/2025      | Amazon Bedrock:<br/><https://ap-southeast-1.console.aws.amazon.com/bedrock>                                                                                                                                                                                   |
| 6   | - Khởi tạo và cấu hình Amazon RDS: <br>&emsp; + Chọn loại cơ sở dữ liệu phù hợp với dự án <br>&emsp; + Thiết lập thông số chính (tài khoản, VPC, security group) <br>&emsp; + Khởi chạy instance, theo dõi trạng thái và lưu endpoint an toàn <br/> - Xây dựng TextService dựa trên cơ sở dữ liệu: <br>&emsp; + Tạo schema đơn giản chứa bảng từ và câu <br>&emsp; + Viết script nhập dữ liệu ban đầu vào RDS <br>&emsp; + Chỉnh sửa TextService để truy xuất dữ liệu từ database thay vì API ngoài <br>&emsp; + Benchmark và so sánh hiệu suất với phương pháp cũ <br>                                                                                                                                                        | 09/19/2025 | 09/19/2025      | Aurora and RDS:<br/><https://ap-southeast-1.console.aws.amazon.com/rds>                                                                                                                                                                                       |

### Thành tựu tuần 2:

- Hoàn tất việc xác định phạm vi cho game đánh máy đầu tiên:

  - Tính năng chính
  - Ranh giới microservice
  - Backlog nền
  - Phân công sở hữu

- Ghi lại công thức tiêu chuẩn cho WPM và độ chính xác.
- Tạo kho mã chung và thiết lập cấu trúc đa ngôn ngữ cơ bản.
- Hoàn thiện ER diagram và phác thảo schema quan hệ.
- Hoàn thành bản FastAPI prototype (sinh văn bản, ghép câu, chat) và kiểm thử qua Swagger UI.
- Thiết lập AWS Budgets kèm cảnh báo.
- Nắm vững các khái niệm nền tảng AWS:
  - Lambda (function URL)
  - VPC (subnet, IGW, NAT, Flow Logs)
  - Peering và transit gateway
  - Load balancing cơ bản
- Khám phá các mô hình Bedrock, chọn mô hình phù hợp và xác thực cách tạo prompt.
- Khởi chạy RDS, xây schema và thêm dữ liệu mẫu.
- Tái cấu trúc TextService sang truy xuất DB và thực hiện benchmark đầu tiên.
- Bắt đầu quy trình vận hành: phân công vai trò, chú trọng hiệu suất, và định hướng mở rộng.
