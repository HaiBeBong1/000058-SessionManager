---
title: "Create EventBridge"
weight: 1
chapter: false
pre: "<b>7.1. </b>"
draft: false
---

#### Create EventBridge Rule **eventb_iadr** to receive events from GuardDuty and send to Lambda

1. Access [Amazon EventBridge Console](https://console.aws.amazon.com/events/).  
    + Click **Create rule**.  
![EventBridge](/000058-SessionManager/images/7.EventBridge/1.png)  

2. Define the Rule information.  
    + **Name**: `eventb_iadr`  
    + **Description**: `Eventbridge from GuardDuty to Lambda`  
    + **Event bus**: select `default`  
    + **Rule type**: select **Rule with an event pattern**  
    + Click **Next**.  
![EventBridge](/000058-SessionManager/images/7.EventBridge/2.png)  

3. Build Event Pattern.  
    + **Event source**: select **Other**  
    + **Creation method**: select **Custom pattern (JSON editor)**  
    + Enter the following JSON content:  
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
![EventBridge](/000058-SessionManager/images/7.EventBridge/3.png)  
    + Click **Next**.  
![EventBridge](/000058-SessionManager/images/7.EventBridge/4.png)  

4. Select target as Lambda function.  
    + **Target type**: AWS service  
    + **Select a target**: Lambda function  
    + **Target location**: Target in this account  
    + **Function**: `aird_lambda`  
    + Select **Create a new role for this specific resource**  
    + Click **Next**.  
![EventBridge](/000058-SessionManager/images/7.EventBridge/5.png)  

5. (Optional) Add tags if needed, then click **Next**.  
![EventBridge](/000058-SessionManager/images/7.EventBridge/6.png)  

6. Review the configuration, then click **Create rule**.  
![EventBridge](/000058-SessionManager/images/7.EventBridge/7.png)  

7. Confirm the rule has been created successfully.  
![EventBridge](/000058-SessionManager/images/6.clean7.EventBridge/8.png)  

8. Confirm the rule creation success message.  
    + The screen shows a green notification: `Rule eventb_iadr was created successfully`.  
![EventBridge](/000058-SessionManager/images/7.EventBridge/9.png)
