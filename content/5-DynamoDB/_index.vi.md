---
title : "Amazon DynamoDB"
date: 2025-06-18
weight : 5 
chapter : false
pre : " <b> 5. </b> "
---

> Tạo bảng DynamoDB để lưu trữ thông tin các EC2 instance bị xâm nhập.

 1. Truy cập DynamoDB
    - Vào [DynamoDB console](https://console.aws.amazon.com/dynamodb/home)  
    - Click **Create table**

![DynamoDB](/images/5.DynamoDB/1.png)

2. Nhập thông tin bảng
    - **Table name**: `CompromisedInstances`  
    - **Partition key**: `InstanceId` (String)  
    - **Sort key**: `Timestamp` (String)  
    - Chọn **Default settings**

![DynamoDB](/images/5.DynamoDB/2.png)

3. Hoàn tất tạo bảng
    - Kéo xuống cuối trang, click **Create table**

![DynamoDB](/images/5.DynamoDB/3.png)

4. Xác nhận bảng đã tạo thành công
    - Kiểm tra trạng thái bảng là **Active**  
    - Bảng hiển thị đúng `Partition key` và `Sort key`

![DynamoDB](/images/5.DynamoDB/4.png)


