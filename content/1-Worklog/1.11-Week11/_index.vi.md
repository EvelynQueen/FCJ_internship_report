---
title: "Week 11 Worklog"
date: "`r Sys.Date()`"
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

### Mục tiêu Tuần 11:

- Tham gia buổi sinh hoạt cộng đồng AWS để tìm hiểu sâu hơn về các dịch vụ nâng cao và thực tiễn tối ưu.
- Xây dựng dịch vụ xử lý văn bản dạng serverless với thiết kế bảng DynamoDB và cấu hình IAM.
- Phát triển các hàm truy vấn cơ sở dữ liệu hỗ trợ phân trang và bộ lọc điều kiện.
- Tạo hệ thống cache trong bộ nhớ và kiểm tra tính hợp lệ của yêu cầu API.
- Tích hợp Amazon Bedrock Agent để tạo nội dung đoạn văn bằng AI.
- Thiết lập các công cụ giám sát và gỡ lỗi cho ứng dụng serverless.
- Phát triển API GraphQL với AWS AppSync và các resolver dùng DynamoDB.

### Nhiệm vụ trong tuần:

| Day | Task                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | Start Date | Completion Date | Reference Material                                                                                                                            |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| 2   | - **Tham dự sự kiện “AWS Cloud Mastery Series #2”**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | 11/17/2025 | 11/17/2025      |
| 3   | - **Khởi tạo nền tảng serverless cho text service:** <br>&emsp; + Tạo bảng DynamoDB `wordsntexts` với partition key dạng chuỗi để lưu từ và đoạn văn <br>&emsp; + Cấu hình IAM cho phép `dynamodb:Scan`, `dynamodb:Query` và ghi log CloudWatch <br>&emsp; + Tạo khung Lambda handler ban đầu và thiết lập các đối tượng kết nối DB qua `boto3` <br><br> - **Xây dựng các hàm truy xuất cơ sở dữ liệu:** <br>&emsp; + Tạo `fetch_words_from_db` sử dụng Scan cùng `LastEvaluatedKey` cho phân trang <br>&emsp; + Tạo `fetch_paragraph_from_db` áp dụng filter cho loại nội dung và độ dài                                                                                                                                                                                                                                                                   | 11/18/2025 | 11/18/2025      |
| 4   | - **Phát triển cơ chế cache và xử lý dữ liệu:** <br>&emsp; + Tạo cache trong bộ nhớ với TTL 300 giây để giảm tần suất Scan <br>&emsp; + Xây dựng `get_random_words` để lấy dữ liệu từ cache hoặc DB và chọn ngẫu nhiên <br>&emsp; + Xây dựng `get_paragraph` để kiểm soát độ dài (1–3) và tách chuỗi nội dung thành danh sách từ <br><br> - **Thực hiện kiểm tra dữ liệu vào và chuẩn hóa phản hồi API:** <br>&emsp; + Viết `Decimal_encoder` để tuần tự hóa giá trị số của DynamoDB sang JSON <br>&emsp; + Kiểm tra tham số `type` và `count` nhằm xử lý các lỗi `TypeError` và `ValueError` <br>&emsp; + Chuẩn hóa cấu trúc JSON trả về cùng mã trạng thái và header nhất quán                                                                                                                                                                            | 11/19/2025 | 11/19/2025      |
| 5   | - **Tích hợp Amazon Bedrock Agent để tạo nội dung sinh:** <br>&emsp; + Mở rộng quyền IAM để cho phép `bedrock:InvokeAgent` và liên kết Agent ID `HUEBUXSALX` <br>&emsp; + Khởi tạo client `bedrock-agent-runtime` và triển khai lời gọi `invoke_agent` kèm quản lý phiên <br>&emsp; + Phát triển xử lý dữ liệu streaming và ghép nối các byte đã giải mã <br><br> - **Thử nghiệm prompt và mô hình:** <br>&emsp; + Thiết kế prompt đảm bảo Agent trả về đúng ba đoạn văn ngăn cách bằng dòng trống <br>&emsp; + Thử nhiều mô hình để duy trì định dạng ổn định cho logic tách nội dung <br>&emsp; + Tạo bộ xử lý phân tách đầu ra AI                                                                                                                                                                                                                        | 11/20/2025 | 11/20/2025      |
| 6   | - **Giám sát và gỡ lỗi ứng dụng serverless bằng CloudWatch và X-Ray** <br>&emsp; + Phân tích log Lambda trong CloudWatch để tìm và khắc phục lỗi chạy <br>&emsp; + Tạo metric tùy chỉnh để theo dõi hiệu năng theo nhu cầu ứng dụng <br>&emsp; + Thiết lập CloudWatch Alarms để cảnh báo khi vượt ngưỡng quan trọng <br>&emsp; + Bật X-Ray để quan sát service map và phát hiện điểm nghẽn độ trễ <br><br> - **Xây dựng API GraphQL với AWS AppSync và DynamoDB resolvers** <br>&emsp; + Chuẩn bị môi trường AppSync và kết nối DynamoDB làm nguồn dữ liệu <br>&emsp; + Xây dựng các resolver cho thao tác ghi và đọc dữ liệu đơn lẻ <br>&emsp; + Tạo resolver Update và Delete để quản lý vòng đời dữ liệu <br>&emsp; + Thực thi Scan và Query để hỗ trợ lấy dữ liệu hàng loạt <br>&emsp; + Tạo resolver phức tạp để xử lý cấu trúc dữ liệu dạng lồng nhau | 11/21/2025 | 11/21/2025      | CloudWatch and X-Ray Monitoring: <br> <https://000085.awsstudygroup.com/> <br> AppSync GraphQL APIs: <br> <https://000086.awsstudygroup.com/> |

### Thành tựu Tuần 11:

- Tham gia chương trình “AWS Cloud Mastery Series #2” để mở rộng hiểu biết về các tính năng nâng cao của AWS.

- Hoàn chỉnh hạ tầng serverless cho ứng dụng luyện gõ văn bản:

  - Tạo bảng DynamoDB `wordsntexts` với partition key dạng chuỗi, chứa khoảng 64.726 mục từ và đoạn văn.
  - Cấu hình IAM để kích hoạt Scan/Query DynamoDB và ghi log CloudWatch.
  - Thiết lập Lambda (128 MB RAM, timeout 15s) với đối tượng kết nối DB qua `boto3`.

- Hoàn thiện các thành phần truy vấn cơ sở dữ liệu:

  - Viết `fetch_words_from_db` dùng Scan kết hợp phân trang bằng `LastEvaluatedKey`.
  - Viết `fetch_paragraph_from_db` với bộ lọc độ dài (ngắn: 10–25, trung bình: 25–60, dài: 60+ từ).

- Tối ưu hiệu năng và xử lý yêu cầu:

  - Tạo hệ thống cache TTL 300 giây để giảm tải Scan cho ~500 yêu cầu/giờ.
  - Xây dựng `get_random_words` và `get_paragraph` với lấy mẫu ngẫu nhiên và giới hạn độ dài (1–3).
  - Viết `Decimal_encoder` để chuyển đổi số DynamoDB sang JSON đúng chuẩn.
  - Tăng kiểm tra hợp lệ cho tham số `type` và `count`.
  - Chuẩn hóa phản hồi API với mã trạng thái và header đồng nhất.

- Tích hợp Amazon Bedrock Agent để sinh đoạn văn:

  - Cập nhật IAM bao gồm quyền `bedrock:InvokeAgent` và liên kết Agent ID `HUEBUXSALX`.
  - Thiết lập gọi `bedrock-agent-runtime` kèm quản lý phiên.
  - Xây dựng bộ xử lý tái tạo nội dung từ các luồng byte.
  - Chuẩn bị prompt để tạo ba đoạn văn tách bằng dòng trống.
  - Thêm logic tách nội dung AI sau khi sinh.

- Hoàn thiện khả năng giám sát và phân tích lỗi:

  - Rà soát log CloudWatch để tìm lỗi thực thi.
  - Thêm metric tùy chỉnh theo nhu cầu ứng dụng.
  - Thiết lập cảnh báo CloudWatch cho ngưỡng nghiêm trọng.
  - Kích hoạt X-Ray để phân tích đường đi dịch vụ và độ trễ.

- Phát triển API GraphQL với AWS AppSync:
  - Chuẩn bị môi trường và kết nối DynamoDB làm datasource.
  - Tạo resolver cho CRUD (Tạo/Đọc/Cập nhật/Xóa).
  - Tạo Scan và Query resolver cho truy vấn số lượng lớn.
  - Phát triển resolver phức tạp cho cấu trúc dữ liệu lồng nhau.
