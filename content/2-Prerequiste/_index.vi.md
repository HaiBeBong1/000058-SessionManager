---
title : "Các bước chuẩn bị"
date: 2025-07-08
weight : 2
chapter : false
pre : " <b> 2. </b> "
---
## 2. Các bước chuẩn bị ban đầu
Trước khi bắt đầu xây dựng hệ thống phát hiện và phản ứng bảo mật tự động, bạn cần chuẩn bị đầy đủ các điều kiện tiên quyết về tài khoản **AWS**, cũng như thực hiện một số bước thiết lập về môi trường, tài nguyên và quyền truy cập để đảm bảo quá trình triển khai diễn ra thuận lợi và chính xác.

### 2.1. Yêu cầu tài khoản và quyền truy cập
Để triển khai hệ thống này, bạn cần một tài khoản AWS đáp ứng các điều kiện sau:
- **Tài khoản AWS đã kích hoạt billing** (có thể là tài khoản cá nhân, tài khoản trong chương trình AWS Educate hoặc Free Tier).
- Có quyền truy cập **AdministratorAccess** hoặc tối thiểu các quyền cần thiết cho:
  - EC2, S3, Lambda, SNS, DynamoDB, EventBridge, IAM, GuardDuty.
- **Khuyến khích:** Bật **Multi-Factor Authentication (MFA)** cho tài khoản root hoặc IAM user để tăng cường bảo mật.
### 2.2. Phạm vi Free Tier của AWS
Workshop này được thiết kế để chạy **toàn bộ trong giới hạn AWS Free Tier**, không phát sinh chi phí nếu bạn chưa vượt hạn mức sử dụng miễn phí.

**Bảng: Mức sử dụng tài nguyên so với giới hạn Free Tier**

| Dịch vụ (Service)   | Giới hạn Free Tier                                 | Mức sử dụng trong Workshop            |
|---------------------|----------------------------------------------------|----------------------------------------|
| **Amazon S3**       | 5GB lưu trữ, 20,000 lượt GET/tháng                 | < 1GB, < 100 lượt truy cập             |
| **AWS Lambda**      | 1 triệu request/tháng, 400,000 GB-seconds          | < 1,000 request                        |
| **Amazon SNS**      | 1,000 thông báo email/tháng                        | < 50 thông báo                         |
| **Amazon DynamoDB** | 25GB lưu trữ, 25 RCU/WCU                           | < 1GB, chỉ vài thao tác ghi            |
| **Amazon GuardDuty**| Free trong 30 ngày (dùng thử cho lần đầu bật)     | Trong thời gian dùng thử              |
| **Amazon EventBridge** | Miễn phí 100,000 sự kiện/tháng                  | < 1,000 sự kiện                        |

### 2.3. Chuẩn bị môi trường thực hành

Trước khi bắt đầu các bước cấu hình dịch vụ, bạn cần chuẩn bị một môi trường thực hành tối thiểu như sau:

- **Khu vực (Region):**  
  Khuyến nghị sử dụng khu vực `us-east-1` hoặc khu vực gần bạn nhất để giảm độ trễ và tăng tính tương thích với các dịch vụ.

- **Đặt tên tài nguyên:**  
  Để dễ quản lý, nên tuân theo quy tắc đặt tên thống nhất. Ví dụ:
  - EC2 Instance: `CompromisedEC2`, `MaliciousEC2`
  - S3 Bucket: `threat-list-[your-unique-id]`
  - IAM Role: `LambdaSecurityRole`
  - Lambda Function: `IsolateInstance`
  - EventBridge Rule: `GuardDutyToLambdaRule`
  - SNS Topic: `GuardDutyNotifications`
  
- **Tài khoản email hợp lệ:**  
  Để nhận thông báo từ Amazon SNS, bạn cần có một địa chỉ email có thể nhận thư và xác nhận đăng ký.

- **Kiểm tra quyền truy cập IAM:**  
  Đảm bảo user/role bạn đang dùng có quyền tạo và chỉnh sửa các dịch vụ nêu trên. Nếu sử dụng IAM user, kiểm tra lại các policy đính kèm.

> 📌 Lưu ý: Hạn chế sử dụng tài khoản root để triển khai — thay vào đó nên sử dụng IAM user có quyền phù hợp.
