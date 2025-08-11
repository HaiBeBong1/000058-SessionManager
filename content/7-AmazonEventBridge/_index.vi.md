---
title : "Amazon EventBridge"
weight : 7
chapter : false
pre: "<b> 7. </b>"
---

**Amazon EventBridge** là dịch vụ bus sự kiện (event bus) được quản lý hoàn toàn bởi AWS, cho phép bạn kết nối các ứng dụng bằng cách định tuyến sự kiện từ các nguồn (như GuardDuty) đến các dịch vụ đích (như Lambda, SNS).  
**EventBridge** sẽ đóng vai trò **bắt sự kiện cảnh báo bảo mật** từ GuardDuty và **kích hoạt Lambda** để xử lý tự động.

## Nội Dung
  - [Tạo rule EventBridge](7.1-EventBridgeConfiguration/)
  - [Cấu hình trigger cho Lambda](7.2-IntegrateWithLambda/)

