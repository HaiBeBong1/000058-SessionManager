---
title : "Xây dựng hệ thống tự động gửi cảnh báo bảo mật đa tầng trên AWS "
date: 2025-06-18
weight : 1 
chapter : false
---

# Xây dựng hệ thống tự động gửi cảnh báo bảo mật đa tầng trên AWS

Trong môi trường điện toán đám mây, việc phát hiện và phản ứng kịp thời với các mối đe dọa bảo mật là yếu tố then chốt để bảo vệ hệ thống.  
Workshop này sẽ hướng dẫn bạn xây dựng một **giải pháp giám sát và cảnh báo bảo mật đa tầng** trên AWS, kết hợp nhiều dịch vụ để **tự động phát hiện, cô lập, và thông báo khi phát hiện sự cố**.

![introduce](/images/AWS.png)
Giải pháp sẽ sử dụng:
- **Amazon GuardDuty** để phát hiện hành vi bất thường và mối đe dọa tiềm ẩn.
- **Amazon EventBridge** để xử lý và phân phối sự kiện bảo mật.
- **AWS Lambda** để tự động hóa các hành động phản ứng (như cô lập và dừng EC2 bị xâm nhập).
- **Amazon SNS** để gửi cảnh báo đến nhóm vận hành.
- **Amazon S3** và **DynamoDB** để lưu trữ thông tin sự cố và log liên quan.

### Nội dung

 1. [Giới thiệu](1-introduce/)
 2. [Các bước chuẩn bị](2-Prerequiste/)
 3. [Tạo S3](3-CreateS3/)
 4. [Bật AmazonGuardDuty](4-AmazonGuardDuty/)
 5. [Tạo Amazon lambda](5-AWSLambda/)
 6. [Amazon EventBridge](6-AmazonEventBridge/)
 7. [Tạo SNS](7-SimpleNotificationService/)
 8. [Kết quả đạt được](8-AchievedResult/)
 9. [Dọn dẹp tài nguyên](9-CleanUpResources/)
