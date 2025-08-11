---
title: "Integrate with Lambda"
weight: 2
chapter: false
pre: "<b>8.2. </b>"
draft: false
---

#### Configure Lambda Destination for function **aird_lambda**

1. Open the details page of the Lambda function **aird_lambda** in the [AWS Lambda Console](https://console.aws.amazon.com/lambda/).  
   + Ensure the function already has the **EventBridge (CloudWatch Events)** trigger attached.  
   + Click **Add destination** to configure the event destination.  

![SNS](/000058-SessionManager/images/8.SNS/9.png)

2. Configure the Destination:  
   + **Source**: Select `Asynchronous invocation`.  
   + **Condition**: Select `On success` (send notification when execution is successful).  
   + **Destination type**: Select `SNS topic`.  
   + **Destination**: Enter the ARN of the SNS Topic `arn:aws:sns:ap-southeast-1:070653981874:Automated_idr_SNS`.  
   + Click **Save** to save the configuration.  

![SNS](/000058-SessionManager/images/8.SNS/10.png)

3. Verify the configuration:  
   + After saving, the Lambda function’s diagram will display the `SNS` destination next to the EventBridge trigger.  
   + This ensures that whenever the Lambda executes successfully, a notification will be sent to the SNS Topic.  

![SNS](/000058-SessionManager/images/8.SNS/11.png)
