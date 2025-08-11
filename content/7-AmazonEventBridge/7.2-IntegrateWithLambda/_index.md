---
title: "Integrate with Lambda"
weight: 2
chapter: false
pre: "<b>7.2. </b>"
draft: false
---

#### Add EventBridge Trigger for Lambda **aird_lambda**

1. Open [AWS Lambda Console](https://console.aws.amazon.com/lambda/home) and select the **aird_lambda** function.  
   + In the **Function overview** section, click **Add trigger**.

![EventBridge](/images/7.EventBridge/10.png)  

2. Configure the Trigger using EventBridge.  
      + **Trigger type**: select **EventBridge (CloudWatch Events)**.  
      + In the **Rule** section, choose **Existing rules**.  
      + Under **Existing rules**, select the rule you created earlier: `eventb_iadr` (the ARN will appear in the selection box).  
      + Verify that the **Rule description** and **Event pattern** are correct.  
      + Click **Add** to add the trigger.

![EventBridge](/images/7.EventBridge/11.png)  

3. Confirm the trigger was successfully added.  
      + The screen shows a green message: *“The trigger eventb_iadr was successfully added to function aird_lambda.”*  
      + In the **Function overview** diagram, you will see the **EventBridge (CloudWatch Events)** node connected to the **aird_lambda** function.

![EventBridge](/images/7.EventBridge/12.png)
