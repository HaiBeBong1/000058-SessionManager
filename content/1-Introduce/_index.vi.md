---
title : "Giới thiệu"
date: 2025-06-18
weight : 1 
chapter : false
pre : " <b> 1. </b> "
---

##  Mục tiêu Workshop
Trong workshop này, chúng ra sẽ học cách xây dựng một **hệ thống phát hiện và phản ứng bảo mật tự động** trên nền tảng đám mây AWS. Hệ thống có thể phát hiện các hành vi đáng ngờ như port scanning, đăng nhập trái phép vào EC2 hoặc truy cập bất thường đến tài nguyên. Khi phát hiện, hệ thống sẽ **gửi cảnh báo gần như ngay lập tức**, và **tự động phản ứng để chặn IP tấn công** bằng cách dùng GuardDuty → EventBridge → Lambda.

Toàn bộ pipeline sử dụng các dịch vụ serverless như:
- **Amazon GuardDuty**: Phát hiện mối đe dọa
- **Amazon EventBridge**: Lắng nghe và kích hoạt sự kiện
- **AWS Lambda**: Xử lý logic phản ứng
- **Amazon SNS / DynamoDB**: Gửi cảnh báo đa tầng
![introduce](/images/AWS.png)
## Kiến trúc hệ thống
**GuardDuty**Phát hiện mối đe dọa
**EventBridge**Bắt sự kiện đe dọa
**Lambda**Phân tích & phản ứng
**SNS** email
**DynamoDB**
         
## Luồng hoạt động
1. **GuardDuty** liên tục giám sát các tài nguyên AWS và tạo cảnh báo (Findings) khi phát hiện hành vi bất thường.
2. **EventBridge** bắt sự kiện `GuardDuty Finding` và kích hoạt hàm **Lambda** tương ứng.
3. **Lambda** thực hiện các hành động như:
   - Phân tích nội dung cảnh báo
   - Trích xuất địa chỉ IP tấn công
   - Gọi API để chặn IP bằng cách chỉnh sửa NACL hoặc Security Group
   - Lưu log vào **DynamoDB**
   - Gửi thông báo qua **SNS** (email)


##  Nội dung workshop
1. Kích hoạt **GuardDuty** và kiểm tra cảnh báo mẫu  
2. Tạo **EventBridge Rule** để bắt cảnh báo từ GuardDuty  
3. Viết **hàm Lambda** để xử lý: phân tích cảnh báo, chặn IP  
4. Gửi cảnh báo đến **SNS, DynamoDB**
5. Kiểm thử hệ thống bằng hành vi tấn công giả lập (`nmap`)  
6. Tổng kết & mở rộng: tự động mở lại IP, đặt TTL, phân quyền IAM chặt chẽ hơn
