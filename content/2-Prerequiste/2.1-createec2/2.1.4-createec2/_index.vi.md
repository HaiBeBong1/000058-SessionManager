---
title : "Tạo EC2 Instance"
date: 2025-06-18
weight : 4
chapter : false
pre : " <b> 2.1.4 </b> "
---

1. Truy cập [giao diện quản trị dịch vụ EC2](https://console.aws.amazon.com/ec2/v2/home)
  + Click **Instances**.
  + Click **Launch instances**.

![EC2](/000058-SessionManager/images/2.prerequisite/image2.2.36.png)

2. Tại Instance
  + Đặt tên and tags, nhập **EC2 **
  + Đăt Number of instances là: **2**
  + Chọn Quick Start
  + Chọn Amazon Linux 2
  + Chọn phiên bản AMI phù hợp
  
![EC2](/000058-SessionManager/images/2.prerequisite/image2.2.37.png)

3. Cấu hình Instance và Key Pair
 + Click chọn Instance type **t2.micro**.
 + Click Create new key pair.
 
![EC2](/000058-SessionManager/images/2.prerequisite/image2.2.38.png)

4. Tạo Key Pair mới
  + Key pair name: Nhập **kpair**
  + Key pair type: Chọn **RSA**
  + Private key format: Chọn .pem
  + Click **Create key pair**

![EC2](/000058-SessionManager/images/2.prerequisite/image2.2.39.png)

5.5. Thiết lập Network Settings
  + VPC - required: Chọn **vpc-0bed0339b78a7b96e (security-workshop-vpc)**
  + Subnet: Chọn **Public-Subnet**
  + Auto-assign public IP: Chọn **Enable**
  + Security Group: **Chọn Public subnet - SG**
  + Click **Launch instance**

![EC2](/000058-SessionManager/images/2.prerequisite/11.png)

6. Hoàn tất khởi tạo
  + Đổi tên **MalC2** và **Compromised_EC**
![EC2](/000058-SessionManager/images/2.prerequisite/image2.2.41.png)

