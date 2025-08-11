---
title: "Kết quả đạt được"
date: 2025-06-18
weight: 9
chapter: false
pre: "<b>9.</b>"
---

## Kết quả 

1. **Liệt kê các EC2 instance**  
   + Hai EC2 instance được tạo thuộc Security Group **Public subnet - SG**.  
![result](/000058-SessionManager/images/9.result/1.png)
2. **Tick vào Compromised_EC2**  
   + Chn instance **Compromised_EC2**, sau đó nhấn **Connect**.  
![result](/000058-SessionManager/images/9.result/8.1.png)
3. **Kết nối SSH**  
   + Sử dụng lệnh SSH bên dưới để kết nối vào EC2:  
   + Click **Yes**  
   ```bash
   ssh -i "kpair.pem" ec2-user@47.128.65.71
      ```
![result](/000058-SessionManager/images/9.result/5.1.png)
![result](/000058-SessionManager/images/9.result/6.1.png)
4. Kiểm tra người dùng & chuyển root
   + dùng các lệnh sau:
```bash
whomi            # gõ sai -> lỗi "command not found"
whoami           # đúng: trả về 'ec2-user'
sudo su          # chuyển sang user 'root'
whoami           # xác nhận: 'root'
nano payload.sh  # tạo script
```
![result](/000058-SessionManager/images/8.result/7.1.png)
5.Nội dung script
```bash
#!/bin/bash
for j in {1..10}; do
  sudo nmap -sT -Pn 13.229.210.16
done
```
+ Lấy địa chỉ của **MalC2** IPv4: 13.229.210.16 
![result](/000058-SessionManager/images/9.result/9.1.png)
![result](/000058-SessionManager/images/9.result/10.1.png)

6. Lưu lại file payload.sh :
   + Nhấn Ctrl + O (Write Out)
   + Nhấn Enter để xác nhận tên file (payload.sh)
   + Nhấn Ctrl + X để thoát khỏi nano

7.  Chạy lệnh 

```bash
chmod +x payload.sh
./payload.sh
```
![result](/000058-SessionManager/images/9.result/20.png)



9. Kết quả này lặp lại ổn định trong nhiều lần quét, chứng tỏ cấu hình mạng hiện tại chỉ cho phép truy cập SSH và chặn toàn bộ dịch vụ khác.

![result](/000058-SessionManager/images/9.result/11.png)
10. Trạng thái EC2 sau khi xử lý
Sau khi xác định **Compromised_EC2** có khả năng bị khai thác, instance này đã được gán sang **Security Group “Sg-isolated”** để chặn toàn bộ kết nối mạng.
- **MalC2**  
  - Trạng thái: **Running** (2/2 checks passed)  

- **Compromised_EC2**  
  - Trạng thái: **Stopping** (đang dừng)  

![result](/000058-SessionManager/images/9.result/12.png)

11. Cô lập EC2 qua Security Group
   + Sau khi xác định **Compromised_EC2** có khả năng bị khai thác, instance này đã được gán sang **Security Group “Sg-isolated”** để chặn toàn bộ kết nối mạng.
![result](/000058-SessionManager/images/9.result/13.png)
   + Biện pháp này giúp:
   - **Ngăn chặn rủi ro lan rộng** sang các tài nguyên khác.
   - **Bảo toàn dữ liệu hiện trường** để điều tra nguyên nhân và phương thức tấn công.
12. Phát hiện từ AWS GuardDuty
AWS GuardDuty đã ghi nhận một sự kiện **Recon:EC2/Portscan** với mức độ **Medium** đối với instance `i-02cc787dd11d0703f` (**Compromised_EC2**).  
![result](/000058-SessionManager/images/9.result/14.png)
13. Chi tiết cảnh báo GuardDuty

Thông tin chi tiết cảnh báo:

   - **Finding ID**: `16cc49ab87e99a0d94f0d379281477d6`  
   - **Type**: `Recon:EC2/Portscan`  
   - **Severity**: `MEDIUM`  
   - **Region**: `ap-southeast-1`  
   - **Thời gian phát hiện**: `08-10-2025 16:36:53`  
   - **Địa chỉ mục tiêu**: `13.229.210.16`  
   - **Resource**: `i-02cc787dd11d0703f`

![result](/000058-SessionManager/images/9.result/15.png)
![result](/000058-SessionManager/images/9.result/16.1.png)
14. AWS SNS đã gửi thông báo xác nhận:
   + Điều này cho thấy quy trình phản ứng sự cố đã thành công: EC2 bị cô lập khỏi mạng và dừng hoạt động, ngăn chặn mọi hoạt động tiếp theo từ nguồn này.
![result](/000058-SessionManager/images/9.result/17.png)

15. AWS DynamoDB đã lưu lại 
   + Click vào **Table**
   + Click vào **Compromisedlnstances**
![result](/000058-SessionManager/images/9.result/18.png)
![result](/000058-SessionManager/images/9.result/19.png)