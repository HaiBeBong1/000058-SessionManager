---
title: "Tích hợp với Lambda"
weight: 2
chapter: false
pre: "<b>8.2. </b>"
draft: false
---

#### Cấu hình Lambda Destination cho hàm **aird_lambda**

1. Mở trang chi tiết hàm Lambda **aird_lambda** trong [AWS Lambda Console](https://console.aws.amazon.com/lambda/).
   + Kiểm tra rằng hàm đã được gắn trigger 
   **EventBridge (CloudWatch Events)**.  
   + Nhấn **Add destination** để cấu hình đích nhận sự kiện.  

![SNS](/images/8.SNS/9.png)


2. Cấu hình Destination:
   + **Source**: Chọn `Asynchronous invocation`.  
   + **Condition**: Chọn `On success` (gửi thông báo khi chạy thành công).  
   + **Destination type**: Chọn `SNS topic`.  
   + **Destination**: Nhập ARN của SNS Topic `arn:aws:sns:ap-southeast-1:070653981874:Automated_idr_SNS`.  
   + Nhấn **Save** để lưu cấu hình.  

![SNS](/images/8.SNS/10.png)


3. Xác nhận cấu hình thành công:
   + Sau khi lưu, tại sơ đồ của hàm Lambda sẽ hiển thị đích `SNS` bên cạnh trigger EventBridge.
   + Điều này đảm bảo mỗi khi Lambda xử lý thành công, một thông báo sẽ được gửi tới SNS Topic.

![SNS](/images/8.SNS/11.png)