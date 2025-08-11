---
title: "Amazon SNS"
weight: 8
chapter: false
pre: "<b>8. </b>"
draft: false
---

**Amazon SNS** là dịch vụ nhắn tin pub/sub (publish-subscribe) được quản lý hoàn toàn bởi AWS, cho phép bạn gửi thông điệp từ các ứng dụng đến nhiều người nhận hoặc hệ thống khác nhau một cách **nhanh chóng, tin cậy và mở rộng linh hoạt**.
Trong phần này, chúng ta sẽ:
- **Tạo chủ đề SNS (Topic)** để làm kênh phân phối thông điệp.
- **Đăng ký người nhận (Subscriber)** qua email hoặc các giao thức khác.
- **Tích hợp SNS với Lambda** để tự động gửi cảnh báo khi có sự kiện bảo mật từ GuardDuty thông qua EventBridge.
## Nội dung
1. [Tạo SNS](8.1-CreateSNS/)
2. [Tích hợp SNS với Lambda](8.2-IntegrateWithLambda/)