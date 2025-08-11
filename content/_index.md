---
title: "Building a Multi-Layered Automated Security Alert System on AWS"
date: 2025-06-18
weight: 1
chapter: false
---

# Building a Multi-Layered Automated Security Alert System on AWS

In a cloud computing environment, timely detection and response to security threats is critical to protecting your systems.  
This workshop will guide you through building a **multi-layered security monitoring and alerting solution** on AWS, integrating multiple services to **automatically detect, isolate, and notify when an incident occurs**.

![introduce](/000058-SessionManager/images/AWS.png)
This solution will use:
- **Amazon GuardDuty** to detect unusual behavior and potential threats.
- **Amazon EventBridge** to process and route security events.
- **AWS Lambda** to automate response actions (such as isolating and stopping compromised EC2 instances).
- **Amazon SNS** to send alerts to the operations team.
- **Amazon S3** and **DynamoDB** to store incident information and related logs.

### Contents

1. [Introduction](1-introduce/)
2. [Prerequisites](2-Prerequiste/)
3. [Create S3](3-CreateS3/)
4. [Enable Amazon GuardDuty](4-AmazonGuardDuty/)
5. [Create AWS Lambda](5-AWSLambda/)
6. [Amazon EventBridge](6-AmazonEventBridge/)
7. [Create SNS](7-SimpleNotificationService/)
8. [Achieved Result](8-AchievedResult/)
9. [Clean Up Resources](9-CleanUpResources/)
