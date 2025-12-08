---
title: "Week 3 Worklog"
date: "'r Sys.Date() '"
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Mục tiêu Tuần 3:

- Hoàn thành các bài lab AWS nền tảng (Site-to-Site VPN, kiến thức cơ bản về EC2).
- Tiếp tục và hoàn tất cả bốn mô-đun của khóa AWS Cloud Technical Essentials.
- Nâng cao kỹ năng thao tác AWS Console và CLI (cấu hình, quản lý key, khám phá region/dịch vụ).
- Phối hợp với nhóm product/design để rà soát và ghi lại UI/UX Figma của TypeRush cho giai đoạn phát triển sắp tới.
- Đánh giá các giải pháp lưu trữ và thống nhất hướng NoSQL mở rộng cho dữ liệu TextService.
- Tạo nguyên mẫu và tích hợp MongoDB (thiết lập môi trường, seeding dữ liệu, chỉnh sửa service, kiểm thử).
- Thiết lập nhịp trao đổi đều đặn với các thành viên First Cloud Journey.

### Nhiệm vụ trong tuần:

| Ngày | Công việc                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | Bắt đầu    | Hoàn thành | Tài liệu tham khảo                                                                                                         |
| ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | ---------- | -------------------------------------------------------------------------------------------------------------------------- |
| 2    | - **Lab 03:** AWS Site-to-Site VPN: <br>&emsp; + Xây dựng hoàn chỉnh môi trường Site-to-Site VPN gồm VPC mới, EC2 làm customer gateway, Virtual Private Gateway và kết nối VPN. <br>&emsp; + Cấu hình và kiểm thử kết nối tunnel. <br><br> - **Lab 04:** Amazon EC2 Fundamentals: <br>&emsp; + Khởi tạo và truy cập EC2 Windows Server và Amazon Linux. <br>&emsp; + Triển khai ứng dụng mẫu “AWS User Management” trên cả hai môi trường để luyện CRUD cơ bản. <br>&emsp; + Khám phá các tính năng EC2 như thay đổi loại instance, quản lý snapshot EBS và tạo AMI tùy chỉnh.                                                                                                                                                                                                                                                  | 09/22/2025 | 09/22/2025 | VPN Lab (Lab 03): <br> <https://000003.awsstudygroup.com/> <br> EC2 Lab (Lab 04): <br> <https://000004.awsstudygroup.com/> |
| 3    | - Bắt đầu khóa AWS Cloud Technical Essentials, hoàn thành hai mô-đun: <br>&emsp; + **Module 1:** Nền tảng Cloud & IAM <br>&emsp;&emsp; - Giải thích điện toán đám mây và lợi ích của nó. <br>&emsp;&emsp; - So sánh môi trường on-premises và cloud. <br>&emsp;&emsp; - Tạo tài khoản AWS và điểm qua các cách tương tác với dịch vụ. <br>&emsp;&emsp; - Trình bày hạ tầng toàn cầu của AWS (Regions, Availability Zones). <br>&emsp;&emsp; - Tìm hiểu và áp dụng các nguyên tắc IAM. <br>&emsp; + **Module 2:** Compute & Networking <br>&emsp;&emsp; - Hiểu các thành phần kiến trúc EC2. <br>&emsp;&emsp; - Phân biệt container và máy ảo. <br>&emsp;&emsp; - Khám phá ưu điểm của serverless. <br>&emsp;&emsp; - Nắm khái niệm mạng cơ bản và các tính năng VPC. <br>&emsp;&emsp; - Tạo một VPC.                            | 09/23/2025 | 09/23/2025 | AWS Cloud Technical Essentials: <br> <https://www.coursera.org/learn/aws-cloud-technical-essentials>                       |
| 4    | - Hợp tác và tài liệu hóa UI/UX Figma của TypeRush: <br>&emsp; + Tham gia buổi review thiết kế đa nhóm để phân tích chi tiết các layout Figma mới. <br>&emsp; + Phân tích từng màn hình chính (đăng nhập/đăng ký, giao diện chơi game, bảng điểm, cài đặt) để hiểu cấu trúc, trạng thái thành phần và hành vi người dùng. <br>&emsp; + Chuẩn bị bộ câu hỏi về khả năng triển khai và các lưu ý kỹ thuật. <br>&emsp; + Bắt đầu chuyển đổi các yếu tố thiết kế thành yêu cầu component hoặc user story sơ bộ. <br><br> - Thảo luận về lưu trữ TextService với Team Lead & xác nhận hướng NoSQL: <br>&emsp; + Trao đổi về giải pháp lưu trữ phù hợp cho từ/câu. <br>&emsp; + So sánh ưu nhược điểm của SQL và NoSQL dựa trên cấu trúc và nhu cầu truy cập. <br>&emsp; + Xác nhận chọn NoSQL do tính linh hoạt và khả năng mở rộng. | 09/24/2025 | 09/24/2025 |                                                                                                                            |
| 5    | - Tích hợp và kiểm thử MongoDB trong TextService Prototype: <br>&emsp; + Thiết lập môi trường MongoDB qua Docker. <br>&emsp; + Chỉnh sửa script seeding để thêm từ/câu vào các collection. <br>&emsp; + Viết lại logic service để truy vấn từ MongoDB thay cho nguồn cũ. <br>&emsp; + Kiểm thử toàn diện để đảm bảo kết nối, ghi và đọc dữ liệu.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | 09/25/2025 | 09/25/2025 |                                                                                                                            |
| 6    | - Hoàn thành hai mô-đun cuối của khóa AWS Cloud Technical Essentials: <br>&emsp; + **Module 3:** Storage & Databases <br>&emsp;&emsp; - Phân biệt file, block, và object storage. <br>&emsp;&emsp; - Hiểu S3 và tạo bucket. <br>&emsp;&emsp; - Giải thích EBS và cách EC2 sử dụng nó. <br>&emsp;&emsp; - Khám phá các dịch vụ cơ sở dữ liệu AWS. <br>&emsp;&emsp; - Nắm DynamoDB và tạo bảng. <br>&emsp; + **Module 4:** Monitoring & High Availability <br>&emsp;&emsp; - Hiểu giá trị monitoring và CloudWatch. <br>&emsp;&emsp; - Tối ưu chi phí và hiệu năng. <br>&emsp;&emsp; - Trình bày Elastic Load Balancing. <br>&emsp;&emsp; - So sánh scaling dọc và scaling ngang. <br>&emsp;&emsp; - Cấu hình giải pháp high availability.                                                                                        | 09/26/2025 | 09/26/2025 | AWS Cloud Technical Essentials: <br> <https://www.coursera.org/learn/aws-cloud-technical-essentials>                       |

### Thành tựu Tuần 3:

- AWS Infrastructure Labs:

  - Xây dựng hoàn chỉnh Site-to-Site VPN (VPC, EC2 gateway, virtual private gateway, kiểm tra tunnel)
  - Hoàn thành EC2 fundamentals (Windows/Linux, triển khai CRUD demo, snapshot, AMI tùy chỉnh)

- Hoàn tất toàn bộ khóa AWS Cloud Technical Essentials (Foundations/IAM, Compute/Networking, Storage/Databases, Monitoring/HA)

- Kỹ năng AWS Console & CLI:

  - Thiết lập tài khoản, quản lý credential và config
  - Điều hướng region/dịch vụ
  - Xử lý key pair và kiểm tra tài nguyên

- Tài liệu hóa UI/UX TypeRush:

  - Rà soát các màn Figma chính và luồng điều hướng
  - Ghi lại trạng thái component và câu hỏi kỹ thuật
  - Soạn yêu cầu component/user story ban đầu

- Kiến trúc lưu trữ TextService:

  - So sánh SQL và NoSQL cho dữ liệu từ/câu
  - Chốt sử dụng NoSQL vì linh hoạt và mở rộng tốt

- Nguyên mẫu tích hợp MongoDB:
  - Tạo môi trường MongoDB bằng Docker
  - Cập nhật script seeding sang dạng document
  - Refactor service để truy vấn MongoDB
  - Xác thực luồng đọc/ghi đầy đủ
