---
title: "Tạo SNS"
weight: 1
chapter: false
pre: "<b>8.1. </b>"
draft: false
---


#### Tạo Amazon SNS Topic **Automated_idr_SNS** và đăng ký email nhận thông báo
1. Truy cập [giao diện quản trị dịch vụ Amazon SNS](https://console.aws.amazon.com/sns/v3/home).
   + Click **Create topic**.
   + Nhập Create topic **Automated_idr_SNS**
![SNS](/000058-SessionManager/images/8.SNS/1.png)

2. Định cấu hình topic.
   + Chọn loại **Standard**.
   + Tại mục **Name** nhập `Automated_idr_SNS`.
   + Tại mục **Display name** nhập `SNS Topic`.
   + Click **Create topic**.

![SNS](/000058-SessionManager/images/8.SNS/2.png)
![SNS](/000058-SessionManager/images/8.SNS/3.png)
#### Tạo Subscription cho Topic **Automated_idr_SNS**
3. Tại trang chi tiết của topic, chọn **Create subscription**.
![SNS](/000058-SessionManager/images/8.SNS/4.png)


4. Định cấu hình subscription.
   + **Protocol**: chọn `Email`.
   + **Endpoint**: nhập `Tên Mail của mình `.
   + Click **Create subscription**.
![SNS](/000058-SessionManager/images/8.SNS/5.png)

5. Sau khi tạo subscription, trạng thái sẽ là **Pending confirmation**.

![SNS](/000058-SessionManager/images/8.SNS/6.png)

6. Mở email từ AWS Notification và click **Confirm subscription**.
![SNS](/000058-SessionManager/images/8.SNS/7.png)
7. Sau khi xác nhận thành công, hệ thống hiển thị thông báo **Subscription confirmed!**.
![SNS](/000058-SessionManager/images/8.SNS/8.png)
