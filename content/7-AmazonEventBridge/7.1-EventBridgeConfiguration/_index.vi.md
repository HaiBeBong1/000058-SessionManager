---
title: "Tạo EventBridge "
weight: 1
chapter: false
pre: "<b>7.1. </b>"
draft: false
---


#### Tạo EventBridge Rule **eventb_iadr** để nhận sự kiện từ GuardDuty và gửi đến Lambda

1. Truy cập [Amazon EventBridge Console](https://console.aws.amazon.com/events/).
    + Click **Create rule**.
![EventBridge](/images/7.EventBridge/1.png)
2. Định nghĩa thông tin Rule.
    + **Name**: `eventb_iadr`
    + **Description**: `Eventbridge from GuardDuty to Lambda`
    + **Event bus**: chọn `default`
    + **Rule type**: chọn **Rule with an event pattern**
    + Click **Next**.
![EventBridge](/images/7.EventBridge/2.png)
3. Xây dựng Event Pattern.
    + **Event source**: chọn **Other**
    + **Creation method**: chọn **Custom pattern (JSON editor)**
    + Nhập nội dung JSON sau:
    ```json
    {
      "source": ["aws.guardduty"],
      "detail-type": ["GuardDuty Finding"],
      "detail": {
        "severity": [4, 5, 6, 7, 8],
        "resource": {
          "resourceType": ["Instance"]
        }
      }
    }
    ```
  
![EventBridge](/images/7.EventBridge/3.png)
  + Click **Next**.
![EventBridge](/images/7.EventBridge/4.png)
4. Chọn target là Lambda function.
    + **Target type**: AWS service
    + **Select a target**: Lambda function
    + **Target location**: Target in this account
    + **Function**: `aird_lambda`
    + Chọn **Create a new role for this specific resource**
    + Click **Next**.
![EventBridge](/images/7.EventBridge/5.png)

5. (Tùy chọn) Thêm tags nếu cần, sau đó click **Next**.
![EventBridge](/images/7.EventBridge/6.png)

6. Kiểm tra cấu hình, sau đó click **Create rule**.
![EventBridge](/images/7.EventBridge/7.png)

7. Xác nhận Rule đã được tạo thành công.
![EventBridge](/images/6.clean7.EventBridge/8.png)
8. Xác nhận Rule đã được tạo thành công.  
    + Màn hình hiển thị thông báo màu xanh: `Rule eventb_iadr was created successfully`.
![EventBridge](/images/7.EventBridge/9.png)





