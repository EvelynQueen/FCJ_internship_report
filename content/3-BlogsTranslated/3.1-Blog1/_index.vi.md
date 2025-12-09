---
title: "Cách Anuttacon mở rộng khối lượng công việc game được nâng cao bởi AI cho “Whispers from the Star”"
date: "2025-08-14"
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

### AWS Storage Blog

**Tác giả:** Andrew (Qingjie) Ren, Ding Xiao, Nathan Winter, Qiang Li, và Qing Xing Liu  
**Ngày đăng:** 14/08/2025  
**Chuyên mục:** Amazon Elastic Block Store (Amazon EBS), Customer Solutions, Games, Intermediate (200), Storage

---

## Giới thiệu

Ngành công nghiệp game đang trải qua sự tăng trưởng đáng kể, với các trải nghiệm tương tác được điều khiển bởi AI đang thiết lập tiêu chuẩn mới. Anuttacon, một phòng thí nghiệm nghiên cứu độc lập, cam kết phát triển humanistic general intelligence cho phép tương tác liền mạch, theo thời gian thực trên văn bản, giọng nói, hình ảnh, và nhiều hơn nữa. Sứ mệnh của họ là tạo ra AI đa phương thức có khả năng thấu hiểu cảm xúc thực sự và giao tiếp biểu cảm - công nghệ vừa có thể suy nghĩ vừa có thể cảm nhận.

Khi chuẩn bị ra mắt trò chơi được mong đợi, “Whispers from the Star,” Anuttacon đã gặp phải một thách thức phổ biến nhưng quan trọng trong ngành: quản lý các đợt tăng đột biến lưu lượng khổng lồ và không thể dự đoán, đồng thời đảm bảo hiệu năng tối ưu trên nhiều AWS Regions và giải quyết các hạn chế về GPU capacity.

Trong blog này, chúng tôi khám phá cách Anuttacon triển khai thành công kiến trúc scalable cho “Whispers from the Star” bằng các dịch vụ AWS. Giải pháp này đặc biệt phù hợp với các công ty game đối mặt với những vấn đề tương tự về lưu lượng không thể dự đoán và giới hạn tài nguyên GPU. Các nhà phát triển game, kiến trúc sư và lãnh đạo kỹ thuật đang làm việc với ứng dụng game tăng cường AI có thể tìm thấy các mẫu kiến trúc và best practice có giá trị trong phần thảo luận này.

---

## The challenge: beyond traditional scaling

Các phương pháp scaling truyền thống trở nên hạn chế khi phải đối mặt với nhu cầu đặc thù của modern gaming workloads, đặc biệt là những workload được tăng cường bởi AI features. “Whispers from the Star” của Anuttacon đã đưa ra một loạt thách thức về scaling có liên kết chặt chẽ, vượt quá giới hạn của các phương pháp thông thường.

### Dynamic traffic patterns

Trò chơi đã trải qua những đợt tăng đột biến lưu lượng khổng lồ trong giai đoạn launch, thường đạt 10–50 lần so với dung lượng bình thường. Nhu cầu đỉnh điểm này khiến việc dự trữ sẵn toàn bộ instances và storage cần thiết trở nên không khả thi về mặt kinh tế. Chu kỳ tương tác hàng ngày tạo ra các mẫu lưu lượng thay đổi khi người chơi trải nghiệm các tính năng gameplay tăng cường AI tại các thời điểm khác nhau trong ngày, khiến việc phân bổ dung lượng tĩnh trở nên kém hiệu quả.

### Resource constraints

Các AI-enhanced features yêu cầu GPU instances, vốn có mức availability khác nhau giữa các AWS Regions. Đội ngũ cần provision infrastructure chỉ trong vài phút để duy trì trải nghiệm người chơi trong các đợt tăng lưu lượng, đồng thời triển khai dynamic scaling để tránh over-provisioning trong giờ thấp điểm và vẫn bảo đảm capacity trong giờ cao điểm.

### Technical requirements

Kiến trúc cần minimize downtime để đảm bảo người chơi có trải nghiệm nhất quán. Điều này đòi hỏi hiệu năng đồng đều bất kể vị trí địa lý hay giới hạn của hạ tầng nền tảng.

---

## The solution: stateless Multi-Region architecture

Anuttacon triển khai kiến trúc Multi-Region tinh vi sử dụng stateless service được thiết kế để cho phép scaling linh hoạt và quản lý capacity trên các AWS Regions.

### Game service architecture

“Whispers from the Star” bao gồm ba thành phần dịch vụ chính: core game service, renderer service, và inference service. Chúng phối hợp với nhau để mang lại một trải nghiệm game hoàn chỉnh theo các cách sau:

- **Core game service** xử lý các chức năng thiết yếu, chẳng hạn như user login, payment processing, và game state management. Service này duy trì dữ liệu người dùng và tiến trình trò chơi, do đó yêu cầu quản lý state và tính nhất quán dữ liệu một cách cẩn thận.
- **Renderer service** xử lý graphics và các yếu tố hình ảnh, tạo ra visual output mà người chơi nhìn thấy. Service này được thiết kế stateless, cho phép nó chạy trên bất kỳ hạ tầng nào có sẵn mà không cần dữ liệu hoặc cấu hình cụ thể.
- **Inference service** cung cấp sức mạnh cho các tính năng AI-enhanced của trò chơi, chạy các machine learning (ML) models để tạo ra phản hồi và hành vi thông minh. Giống như renderer service, inference service cũng được thiết kế stateless, cho phép nó vận hành trên bất kỳ tài nguyên compute nào có sẵn.

Lựa chọn thiết kế để cả hai service hoàn toàn stateless giúp chúng có thể chạy trên bất kỳ Amazon Elastic Kubernetes Service (Amazon EKS) cluster nào trong bất kỳ AWS Region nào mà không cần data migration hoặc cấu hình đặc thù. Khi có capacity constraints tại một AWS Region, workloads có thể seamlessly move sang các AWS Regions khác có tài nguyên sẵn có.

---

### Architecture components

Giải pháp bao gồm ba thành phần tích hợp hoạt động cùng nhau để cung cấp khả năng scaling và quản lý capacity liền mạch:

1. **Regional EKS clusters**

   - Mỗi AWS Region chứa một EKS cluster độc lập, hoạt động tự trị, scale độc lập dựa trên nhu cầu cục bộ, và duy trì capacity pools cùng phân bổ tài nguyên riêng.
   - Các cluster này bao gồm optimized storage configurations để cho phép faster resource provisioning cho các stateless services.
   - Mỗi Regional cluster sử dụng Amazon EKS để quản lý Kubernetes orchestration, với khả năng tích hợp cùng các AWS services nhằm hỗ trợ seamless scaling và các loại workload đa dạng, bao gồm cả CPU và GPU intensive applications.
   - **Karpenter** cung cấp intelligent node provisioning, tự động chọn optimal instance types, provision nodes chỉ trong vài phút và hỗ trợ nhiều instance families để tránh capacity constraints.

2. **Gateway service**

   - Quản lý routing của các incoming requests trên tất cả Regional clusters.
   - Liên tục giám sát health status của các backend services trên nhiều AWS Regions thông qua active health checks.
   - Phân phối traffic dựa trên real-time usage metrics và health status trên các AWS Regions, đảm bảo optimal load distribution và performance.
   - Đưa ra các quyết định intelligent routing để điều hướng player requests đến regional cluster khỏe mạnh và phù hợp nhất.

3. **Global manager**
   - Cung cấp intelligent orchestration và capacity management trên tất cả regional clusters cùng với các Availability Zones (AZs).
   - Liên tục giám sát usage và capacity constraints ở cả mức Regional và AZ, tự động rebalances target capacity của mỗi cluster để tối ưu resource allocation.
   - Hoạt động phối hợp với gateway service để đảm bảo routing decisions và capacity planning được căn chỉnh trên các AWS Regions và AZs.

---

### Giải quyết thách thức triển khai kỹ thuật: inference cold start

Một trong những thách thức lớn nhất trong inference service là vấn đề cold start. Các AI models và containers liên quan thường có kích thước rất lớn, đôi khi lên đến hàng trăm GB. Nếu không được tối ưu hóa, quy trình này có thể mất hơn 10 phút, tạo ra độ trễ không thể chấp nhận trong các traffic spikes.

Anuttacon đã phát triển phương pháp đa tầng xử lý cold start:

- **Pre-build custom Bottlerocket AMIs** với embedded containers để giảm thời gian tải container.
- **Amazon EBS Provisioned Rate for Volume Initialization** để tăng tốc EBS initialization.
- **Amazon EFS** để tải các large ML models.

Cách parallel loading đảm bảo tổng thời gian từ khi khởi động container đến khi hoàn tất model loading dưới 7 phút — cải thiện đáng kể so với cách triển khai trước đó.

---

### Cross-Region scaling best practices

- Multi-Region deployment tăng fault tolerance và đảm bảo capacity availability.
- Diversified instance families phân tán workloads để tránh capacity constraints.
- Warm pool buffer giữ pre-warmed instances, cung cấp thêm thời gian mở rộng trong traffic spikes.
- Retry mechanisms với Karpenter hỗ trợ automatic retry logic khi xảy ra node provisioning failures.
- Backpressure và queuing giúp intelligent traffic management, xử lý load spikes mượt mà.

---

## Các điểm chính khi thiết kế hạ tầng cho game

- **Stateless service design**: Cho phép true multi-Region flexibility và rapid scaling.
- **Storage optimization**: Pre-loading containers vào custom AMIs và EBS Snapshots, dùng Amazon EFS để load models giúp cải thiện hiệu suất scaling.
- **Multi-Region balancing**: Phân phối traffic dựa trên real-time capacity, tối ưu tài nguyên và đảm bảo trải nghiệm người chơi nhất quán.

---

## Conclusion

Thành công của Anuttacon với “Whispers from the Star” cho thấy thiết kế kiến trúc hợp lý có thể giải quyết các thách thức của modern gaming workloads. Việc tập trung vào stateless service design và tận dụng các khả năng của AWS, đặc biệt là Amazon EBS Provisioned Rate for Volume Initialization, đã giúp họ tạo ra giải pháp scale hiệu quả, quản lý chi phí hợp lý và mang lại trải nghiệm xuất sắc cho người chơi.

---

### Tác giả

**Andrew (Qingjie) Ren**  
Chuyên gia Kiến trúc Giải pháp Cao cấp tại AWS, hỗ trợ khách hàng DNB và ISV xây dựng doanh nghiệp trên AWS, chuyên về kiến trúc đám mây, hiện đại hóa, và các giải pháp dữ liệu & AI.

**Ding Xiao**  
Kiến trúc sư Hạ tầng tại Anuttacon, chuyên về AI và kiến trúc đám mây, đam mê LLMs.

**Nathan Winter**  
Kiến trúc sư Giải pháp Chính tại AWS cho ngành Game, chuyên thiết kế, xây dựng và duy trì giải pháp AWS cho ngành game.

**Qiang Li**  
Trưởng Nhóm Kỹ thuật Game & Backend tại Anuttacon, thúc đẩy đổi mới trong phát triển game dựa trên AI.

**Qing Xing Liu**  
Kỹ sư Vận hành tại Anuttacon, chuyên về kiến trúc đám mây cho các game ứng dụng AI, quản lý hệ thống phân tán và AI quy mô lớn.

---

**TAGS:** Amazon EBS Snapshots, Amazon Elastic Compute Cloud (Amazon EC2), Amazon Elastic Container Registry (Amazon ECR), Amazon Elastic File System (Amazon EFS), Amazon Elastic Kubernetes Service (Amazon EKS), AWS Cloud Storage
