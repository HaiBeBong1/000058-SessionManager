---
title : "Amazon GuardDuty"
date: 2025-06-18
weight : 4 
chapter : false
pre : " <b> 4. </b> "
---

#### Bật Amazon GuardDuty và cấu hình Threat IP List

1. **Bật GuardDuty**  
   - Truy cập [AWS GuardDuty Console](https://console.aws.amazon.com/guardduty/).  
   - Chọn **Amazon GuardDuty - all features** và nhấn **Get started** để kích hoạt dịch vụ.  
![GuardDuty](/000058-SessionManager/images/4.GuardDuty/1.png)



2. **Truy cập mục Lists**  
   - Sau khi kích hoạt thành công, ở menu bên trái, chọn **Settings** → **Lists**.  

![GuardDuty](/000058-SessionManager/images/4.GuardDuty/2.png)



3. **Thêm Threat IP List**  
   - Tại phần **Threat IP list**, nhấn **Add a threat ip list**.  

![GuardDuty](/000058-SessionManager/images/4.GuardDuty/3.png)



4. **Nhập thông tin Threat IP List**  
   - **List name**: `ThreatList`  
   - **Location**: `https://threatlists3.s3.ap-southeast-1.amazonaws.com/ThreatList.txt`  
   - **List format**: `Plaintext`  
   - Chọn **Add list** để lưu.  

![GuardDuty](/000058-SessionManager/images/4.GuardDuty/4.png)



5. **Kích hoạt Threat IP List**  
   - Sau khi thêm thành công, chọn danh sách vừa tạo → **Actions** → **Activate** để kích hoạt.  

![GuardDuty](/000058-SessionManager/images/4.GuardDuty/5.png)