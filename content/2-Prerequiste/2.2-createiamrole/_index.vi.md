---
title : "Tạo IAM Role"
date: 2025-06-18
weight : 2 
chapter : false
pre : " <b> 2.2 </b> "
---

### Tạo IAM Role

Trong bước này chúng ta sẽ tiến hành tạo IAM Role. Trong IAM Role này sẽ được gán policy **AmazonSSMManagedInstanceCore**, đây là policy cho phép máy chủ EC2 có thể giao tiếp với Session Manager.

1. Truy cập vào [giao diện quản trị dịch vụ IAM](https://console.aws.amazon.com/iamv2/)
2. Ở thanh điều hướng bên trái, click  **Roles**.  

![role](/images/2.prerequisite/1.png)

3. Click **Create role**.  

![role1](/images/2.prerequisite/2.png)

4. Click **AWS service** và click **Lambda**. 
  + Click **Next**.  

![role1](/images/2.prerequisite/image2.2.3.png)

5. Gán quyền cho Lambda.  
  + Trong ô Search và chọn **các policy sau**:
      - `AmazonEC2FullAccess`  
      - `AWSLambda_FullAccess`  
      - `AWSLambdaBasicExecutionRole`
      - `CloudWatchEventsFullAccess`
      - `AmazonDynamoDBFullAccess`
  + Click chọn policy.
      - **AmazonEC2FullAccess**.  
      - **AWSLambda_FullAccess**. 
      - **AWSLambdaBasicExecutionRole**
      - **CloudWatchEventsFullAccess**
      - **AmazonDynamoDBFullAccess**.  
  + Click **Next**.  
  + Sau đó nhấn **Next**.
![createpolicy](/images/2.prerequisite/4.png)
![createpolicy](/images/2.prerequisite/5.png)
![createpolicy](/images/2.prerequisite/7.png)
![createpolicy](/images/2.prerequisite/8.png)
![createpolicy](/images/2.prerequisite/6.png)
![createpolicy](/images/2.prerequisite/image2.2.6.png)


createS3


6. Đặt tên cho role

- **Role name:** `aird_IAM`
- **Description:** `Allows Lambda functions to call AWS services on your behalf.`

Sau đó nhấn **Next**.

![create role step 3](/images/2.prerequisite/image2.2.7.png)
7. ** Xác nhận và tạo Role

- Kiểm tra lại các policy đã gán (2 policy ở trên).
- Nhấn **Create role** để hoàn tất.

![create role final confirm](/images/2.prerequisite/image2.2.8.png)
8. Role đã được tạo thành công

- Role sẽ xuất hiện trong danh sách IAM Roles.
- Trusted entity: `lambda.amazonaws.com`

![role created success](/images/2.prerequisite/image2.2.9.png)

