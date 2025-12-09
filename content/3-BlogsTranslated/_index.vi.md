---
title: "Blog Được Dịch"
date: "`r Sys.Date()`"
weight: 3
chapter: false
pre: " <b> 3. </b> "
---

#### Blog tôi đã dịch:

### [Blog 1 - Cách Anuttacon mở rộng khối lượng công việc game được nâng cao bởi AI cho “Whispers from the Star”](3.1-Blog1/)

Blog này giải thích cách Anuttacon triển khai thành công kiến trúc có khả năng mở rộng cho trò chơi được nâng cao bởi AI “Whispers from the Star.” Nó đề cập đến các thách thức như lưu lượng truy cập bất ngờ, giới hạn năng lực GPU và việc mở rộng đa vùng. Kiến trúc sử dụng các dịch vụ không trạng thái, các cụm EKS theo vùng, quản lý toàn cầu và các tối ưu hóa cho vấn đề khởi động lạnh inference bằng AMI Bottlerocket tùy chỉnh, Amazon EBS Provisioned Rate for Volume Initialization và Amazon EFS. Bài viết cung cấp các thực tiễn tốt nhất cho khối lượng công việc game hiện đại, bao gồm thiết kế không trạng thái, tối ưu hóa lưu trữ và cân bằng tài nguyên đa vùng.

### [Blog 2 - Xây dựng hiệu quả các AI agents trên AWS Serverless](3.2-Blog2/)

Blog này giới thiệu về AI agentic và giải thích cách xây dựng các AI agents sẵn sàng triển khai trên môi trường serverless bằng các dịch vụ AWS như Amazon Bedrock AgentCore, AWS Lambda và Amazon ECS. Nó nhấn mạnh sự khác biệt giữa AI agentic và AI phản ứng truyền thống, với khả năng hành vi tự chủ theo mục tiêu, suy luận nhiều bước, quản lý bộ nhớ và tích hợp công cụ. Blog cũng đề cập đến quản lý trạng thái, xác thực, khả năng di động qua các môi trường compute và các thực tiễn quan sát (observability) tốt nhất khi sử dụng Strands Agents SDK.

### [Blog 3 - Đơn giản hóa luân chuyển log với Amazon S3 Express One Zone](3.3-Blog3/)

Blog này hướng dẫn cách triển khai luân chuyển log bằng Amazon S3 Express One Zone. Nó giải thích cách cấu hình Log4j2 và Mountpoint để ghi log trực tiếp vào S3, cho phép luân chuyển log tự động mà không cần lưu trữ cục bộ. Bài viết cung cấp hướng dẫn chi tiết về việc tạo tài nguyên AWS, chuẩn bị môi trường làm việc, viết ứng dụng Java để ghi log, giám sát log và dọn dẹp. Các điểm chính bao gồm ghi log hiệu suất cao, tích hợp S3 liền mạch và sử dụng Mountpoint để chuyển đổi thao tác tệp sang API S3.
