---
title : "Tạo Security Group cho Public và Isolated"
date: 2025-06-18
weight : 3
chapter : false
pre : " <b> 2.1.3 </b> "
---


#### Tạo security group

1. Truy cập [giao diện quản trị dịch vụ VPC](https://console.aws.amazon.com/vpc)
  + Click **Security Group**.  
  + Click **Create security group**.

![SG](/images/2.prerequisite/image2.2.27.png)

2. Cấu hình thông tin cơ bản
  + **Security Group name**: Nhập **Public subnet - SG**
  + **Description**: **Nhập Allow SSH and Ping for servers in public subnet**
  + **VPC**: Chọn **security-workshop-vpc**

![SG](/images/2.prerequisite/image2.2.28.png)

3. Thiết lập Inbound Rules
  + Click Add rule
  + Rule 1:
      - Type: **SSH**
      - Source: **My IP (địa chỉ IPv4 public của bạn)**
  + Rule 2:
      - Type: **All ICMP - IPv4**
      - Source: **Anywhere (cho phép ping từ mọi nơi)**

![SG](/images/2.prerequisite/image2.2.29.png)

4. Xác nhận Outbound Rules và tạo Security Group
  + Click Add rule 
  + Type: **All traffic**  
  + Destination: **Anywhere (0.0.0.0/0)**
  + Click **Create security group**.

![SG](/images/2.prerequisite/image2.2.30.png)

5. Kiểm tra Security Group đã tạo

![SG](/images/2.prerequisite/image2.2.31.png)
#### Tạo isolated security group
1. Truy cập [giao diện quản trị dịch vụ VPC](https://console.aws.amazon.com/vpc)
  + Click **Security Group**.  
  + Click **Create security group**.
  
  ![SG](/images/2.prerequisite/image2.2.32.png)

2. Cấu hình thông tin cơ bản cho Security Group cô lập

  + **Security Group name**: Nhập `sg-isolated`
  + **Description**: Nhập `Security Group to isolate compromised EC2`
  + **VPC**: Chọn lại VPC đã dùng cho bài lab (ví dụ: `security-workshop-vpc`)

  > 🎯 Đây là security group sẽ được gán cho EC2 bị phát hiện có hành vi nguy hiểm — giúp cách ly khỏi toàn bộ mạng.

![SG](/images/2.prerequisite/image2.2.33.png)

3. **Cấu hình Inbound Rules**
  + Click Add rule
  + Rule 1:
      - Type: **SSH**
      - Source: **My IP (địa chỉ IPv4 public của bạn)**

4. **Outbound Rules**
  + Nếu có rule mặc định (All traffic → 0.0.0.0/0), hãy để mặc định

  + Sau khi tạo xong, bạn sẽ thấy SG `sg-isolated` xuất hiện trong danh sách.
  + Bạn có thể dùng SG này cho Lambda hoặc EventBridge để tự động chuyển EC2 bị compromise sang trạng thái cách ly.
  + Nhấn **Create security group** để hoàn tất
![SG](/images/2.prerequisite/image2.2.42.png)

