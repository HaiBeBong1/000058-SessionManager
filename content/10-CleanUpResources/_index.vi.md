---
title: "Clean Up Resources"
date: 2025-06-18
weight: 10
chapter: false
pre: "<b>10.</b>"
---

> Sau khi hoàn tất workshop, bạn cần **xóa tài nguyên** để tránh phát sinh chi phí.

1. Chọn và terminate EC2 instances
- Vào [EC2 console](https://console.aws.amazon.com/ec2/v2/home) → **Instances**  
- Tick chọn **tất cả instance** cần xóa  
- **Instance state** → **Terminate (delete) instance**
![CleanUpResources](/images/10-CleanUpResources/1.png)

2. Xác nhận xóa Instances
- Kiểm tra danh sách Instance ID, cột **Termination protection** phải là *Disabled*  
- Không chọn **Skip OS shutdown** (trừ khi cần dừng khẩn cấp)  
- Click **Terminate** để xóa vĩnh viễn
![CleanUpResources](/images/10-CleanUpResources/2.png)

3. Xóa Security Groups không còn dùng
- Mục **Security Groups** (menu trái)  
- Tick nhóm bảo mật cần xóa  
- **Actions** → **Delete security groups**
![CleanUpResources](/images/10-CleanUpResources/3.png)

4. Xác nhận xóa Security Groups
- Nhập **delete** vào ô xác nhận  
- Click **Delete** để hoàn tất
![CleanUpResources](/images/10-CleanUpResources/4.png)



5. Xóa Key Pair
- Vào **Key Pairs**  
- Tick chọn key pair cần xóa  
- **Actions** → **Delete**
![CleanUpResources](/images/10-CleanUpResources/5.png)


6. Xác nhận xóa Key Pair
- Nhập **delete** vào ô xác nhận  
- Click **Delete**

![CleanUpResources](/images/10-CleanUpResources/6.png)


7. Xóa GuardDuty Findings
- Vào **GuardDuty** → **Findings**  
- Tick chọn tất cả findings  
- **Actions** → **Archive**
![CleanUpResources](/images/10-CleanUpResources/7.png)



8. Xóa Threat IP List trong GuardDuty
- Vào **Lists**  
- Chọn danh sách cần xóa  
- **Actions** → **Delete**

![CleanUpResources](/images/10-CleanUpResources/8.png)


9. Xóa AWS Lambda function
- Vào **Lambda** → **Functions**  
- Tick chọn function cần xóa  
- **Actions** → **Delete**

![CleanUpResources](/images/10-CleanUpResources/9.png)

10. Xác nhận xóa Lambda
- Nhập **confirm** vào ô xác nhận  
- Click **Delete**

![CleanUpResources](/images/10-CleanUpResources/10.png)


11. Xóa S3 Bucket
- Vào **Amazon S3**  
- Chọn bucket cần xóa  
- Click **Delete**
![CleanUpResources](/images/10-CleanUpResources/11.png)

12. Xác nhận xóa Bucket
- Nhập tên bucket vào ô xác nhận  
- Click **Delete bucket**

![CleanUpResources](/images/10-CleanUpResources/12.png)


13. Xóa SNS Topic
- Vào **Amazon SNS** → **Topics**  
- Chọn topic cần xóa  
- Click **Delete**

![CleanUpResources](/images/10-CleanUpResources/13.png)
14. Xóa VPC
- Vào **Your VPCs**  
- Tick chọn VPC cần xóa  
- **Actions** → **Delete VPC**

![CleanUpResources](/images/10-CleanUpResources/14.png)

15. Xác nhận xóa VPC
- Kiểm tra danh sách tài nguyên sẽ bị xóa kèm theo (Internet Gateway, Route Table, Subnet…)  
- Nhập **delete** vào ô xác nhận  
- Click **Delete** để hoàn tất

![CleanUpResources](/images/10-CleanUpResources/15.png)

---

16. Xóa Subnet
- Vào **Subnets**  
- Tick chọn subnet cần xóa  
- **Actions** → **Delete subnet**

![CleanUpResources](/images/10-CleanUpResources/16.png)

17. Xác nhận xóa Subnet
- Nhập **delete** vào ô xác nhận  
- Click **Delete** để hoàn tất

![CleanUpResources](/images/10-CleanUpResources/17.png)

---

18. Xóa IAM Roles
- Vào **IAM** → **Roles**  
- Tick chọn các role không còn sử dụng  
- Click **Delete**

![CleanUpResources](/images/10-CleanUpResources/18.png)

---

19. Xóa DynamoDB Table
- Vào **DynamoDB** → **Tables**  
- Tick chọn table cần xóa  
- Click **Delete**

![CleanUpResources](/images/10-CleanUpResources/19.png)


