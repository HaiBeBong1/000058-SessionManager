---
title : "Tạo Public subnet"
date: 2025-06-18
weight : 2
chapter : false
pre : " <b> 2.1.2 </b> "
---

#### Tạo Public subnet

1. Click **Subnets**.
  + Click **Create subnet**.

![VPC](/images/2.prerequisite/image2.2.12.png)

2. Tại trang **Create subnet**.
  + Tại mục **VPC ID** click chọn **security-workshop-vpc**.
  + Tại mục **Subnet name** điền **Public-Subnet**.
  + Tại mục **Availability Zone** chọn Availability zone đầu tiên.
  + Tại mục **IPv4 CIRD block** điền **10.10.1.0/24**.
  + Click **Create subnet**.
![VPC](/images/2.prerequisite/image2.2.13.png)

3. Kéo xuống cuối trang , click **Create subnet**.

4. Click chọn **Lab Public Subnet**.
  + Click **Actions**.
  + Click **Edit subnet settings**.

![VPC](/images/2.prerequisite/image2.2.14.png)

5. Click chọn **Enable auto-assign public IPv4 address**.
  + Click **Save**.

![VPC](/images/2.prerequisite/image2.2.15.png)

6. Click **Internet Gateways**.
  + Click **Create internet gateway**.
  
![VPC](/images/2.prerequisite/image2.2.16.png)

7. Tại trang **Create internet gateway**.
  + Tại mục **Name tag** điền **igw-workshop**.
  + Click **Create internet gateway**.
  
![VPC](/images/2.prerequisite/image2.2.17.png)

8. Sau khi tạo thành công, click **Actions**.
  + Click **Attach to VPC**.
 
![VPC](/images/2.prerequisite/image2.2.18.png)

9. Tại trang **Attach to VPC**.
  + Tại mục **Available VPCs** chọn **security-workshop-vpc**.
  + Click **Attach internet gateway**.
  + Kiểm tra quá trình attach thành công như hình dưới.

![VPC](/images/2.prerequisite/image2.2.19.png)

10. Tiếp theo chúng ta sẽ tạo một custom route table để gán vào **Lab Public Subnet**.
  + Click **Route Tables**.
  + Click **Create route table**.

![VPC](/images/2.prerequisite/image2.2.20.png)

11. Tại trang **Create route table**.
  + Tại mục **Name**, điền **rtb-public-subnet**.
  + Tại mục **VPC**, chọn **security-workshop-vpc**.
  + Click **Create route table**.

![VPC](/images/2.prerequisite/image2.2.21.png)

12. Sau khi tạo route table thành công.
  + Click **Edit routes**.
  
![VPC](/images/2.prerequisite/image2.2.22.png)

13. Tại trang **Edit routes**.
  + Click **Add route**.
  + Tại mục **Destination** điền 0.0.0.0/0
  + Tại mục **Target** chọn **Internet Gateway** sau đó chọn **Lab IGW**.
  + Click **Save changes**.

![VPC](/images/2.prerequisite/image2.2.23.png)

14. Click tab **Subnet associations**.
  + Click **Edit subnet associations** để tiến hành associate custom routable chúng ta vừa tạo vào **Public-Subnet**.


![VPC](/images/2.prerequisite/image2.2.24.png)

15. Tại trang **Edit subnet associations**. 
  + Click chọn **Lab Public Subnet**.
  + Click **Save associations**.

![VPC](/images/2.prerequisite/image2.2.25.png)

16. Kiểm tra thông tin route table đã được associate với **Public-Subnet** và thông tin route đi internet đã được trỏ đến Internet Gateway như hình dưới.


![VPC](/images/2.prerequisite/image2.2.26.png)
