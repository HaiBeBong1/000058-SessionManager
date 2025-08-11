---
title: "Introduction"
date: 2025-06-18
weight: 1
chapter: false
pre: " <b> 1. </b> "
---

## Workshop Objective
In this workshop, we will learn how to build an **automated security detection and response system** on the AWS cloud platform.  
The system can detect suspicious activities such as port scanning, unauthorized login to EC2 instances, or unusual access to resources. Upon detection, it will **send near real-time alerts** and **automatically respond to block the attacking IP** using GuardDuty → EventBridge → Lambda.

The entire pipeline uses serverless services, including:
- **Amazon GuardDuty**: Threat detection
- **Amazon EventBridge**: Event listening and triggering
- **AWS Lambda**: Response logic processing
- **Amazon SNS / DynamoDB**: Multi-layer alerting

![introduce](/000058-SessionManager/images/AWS.png)

## System Architecture
- **GuardDuty**: Detects threats  
- **EventBridge**: Captures threat events  
- **Lambda**: Analyzes & responds  
- **SNS**: Sends email alerts  
- **DynamoDB**: Stores incident logs  

## Workflow
1. **GuardDuty** continuously monitors AWS resources and generates alerts (Findings) when unusual behavior is detected.  
2. **EventBridge** captures the `GuardDuty Finding` event and triggers the corresponding **Lambda** function.  
3. **Lambda** performs actions such as:  
   - Analyzing the alert content  
   - Extracting the attacking IP address  
   - Calling APIs to block the IP by modifying NACL or Security Group  
   - Logging the incident to **DynamoDB**  
   - Sending notifications via **SNS** (email)  

## Workshop Content
1. Enable **GuardDuty** and check sample alerts  
2. Create an **EventBridge Rule** to capture alerts from GuardDuty  
3. Write a **Lambda function** to process alerts and block IPs  
4. Send alerts to **SNS** and **DynamoDB**  
5. Test the system with simulated attack behavior (`nmap`)  
6. Summary & enhancements: automatically unblock IPs, set TTL, enforce stricter IAM permissions
