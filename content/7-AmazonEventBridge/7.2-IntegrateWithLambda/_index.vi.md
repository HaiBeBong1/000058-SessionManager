---
title: "Tích hợp với Lambda"
weight: 2
chapter: false
pre: "<b>7.2. </b>"
draft: false
---

#### Thêm Trigger EventBridge cho Lambda **aird_lambda**

1. Mở [AWS Lambda Console](https://console.aws.amazon.com/lambda/home) và chọn hàm **aird_lambda**.
   + Ở phần **Function overview**, bấm **Add trigger**.

![EventBridge](/images/7.EventBridge/10.png)
2. Cấu hình Trigger sử dụng EventBridge.
      + **Trigger type**: chọn **EventBridge (CloudWatch Events)**.
      + Ở mục **Rule**, chọn **Existing rules**.
      + Trong **Existing rules**, chọn rule đã tạo: `eventb_iadr` (ARN hiện ra trong ô chọn).
      + Kiểm tra phần **Rule description** và **Event pattern** hiển thị đúng.
      + Bấm **Add** để thêm trigger.

![EventBridge](/images/7.EventBridge/11.png)

3. Xác nhận trigger được thêm thành công.
      + Màn hình hiển thị thông báo màu xanh: *“The trigger eventb_iadr was successfully added to function aird_lambda.”*
      + Trong sơ đồ **Function overview**, thấy nút **EventBridge (CloudWatch Events)** gắn với hàm **aird_lambda**.

![EventBridge](/images/7.EventBridge/12.png)

