---
title: "Amazon SNS"
weight: 8
chapter: false
pre: "<b>8. </b>"
draft: false
---

**Amazon SNS** (Simple Notification Service) is a fully managed pub/sub (publish-subscribe) messaging service from AWS, allowing you to send messages from applications to multiple recipients or other systems **quickly, reliably, and with flexible scalability**.  

In this section, we will:  
- **Create an SNS Topic** to serve as the message distribution channel.  
- **Subscribe recipients** via email or other protocols.  
- **Integrate SNS with Lambda** to automatically send alerts when a security event from GuardDuty is detected through EventBridge.  

## Contents
1. [Create SNS](8.1-CreateSNS/)  
2. [Integrate SNS with Lambda](8.2-IntegrateWithLambda/)
