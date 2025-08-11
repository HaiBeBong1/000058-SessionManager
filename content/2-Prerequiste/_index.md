---
title: "Prerequisites"
date: 2025-07-08
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

## 2. Initial Preparation Steps
Before starting to build the automated security detection and response system, you need to have the necessary **AWS account prerequisites** in place, as well as perform certain environment, resource, and access configurations to ensure the deployment process runs smoothly and accurately.

### 2.1. Account and Access Requirements
To deploy this system, you will need an AWS account that meets the following conditions:
- **AWS account with billing enabled** (can be a personal account, AWS Educate account, or Free Tier account).
- Access rights with **AdministratorAccess** or at least the minimum required permissions for:
  - EC2, S3, Lambda, SNS, DynamoDB, EventBridge, IAM, GuardDuty.
- **Recommended:** Enable **Multi-Factor Authentication (MFA)** for the root account or IAM user to enhance security.

### 2.2. AWS Free Tier Scope
This workshop is designed to operate **entirely within the AWS Free Tier limits**, so there will be no costs incurred if you stay within the free usage limits.

**Table: Resource Usage Compared to Free Tier Limits**

| Service             | AWS Free Tier Limit                                | Workshop Usage                         |
|---------------------|----------------------------------------------------|-----------------------------------------|
| **Amazon S3**       | 5GB storage, 20,000 GET requests/month              | < 1GB, < 100 requests                   |
| **AWS Lambda**      | 1 million requests/month, 400,000 GB-seconds        | < 1,000 requests                        |
| **Amazon SNS**      | 1,000 email notifications/month                     | < 50 notifications                      |
| **Amazon DynamoDB** | 25GB storage, 25 RCU/WCU                            | < 1GB, only a few write operations      |
| **Amazon GuardDuty**| Free for the first 30 days (first-time activation)  | Within free trial period                |
| **Amazon EventBridge** | 100,000 events/month free                        | < 1,000 events                          |

### 2.3. Prepare the Practice Environment
Before configuring the services, you should prepare a minimal practice environment as follows:

- **Region:**  
  It is recommended to use `us-east-1` or the region closest to you to reduce latency and increase compatibility with services.

- **Resource Naming Convention:**  
  To make management easier, follow a consistent naming rule. For example:
  - EC2 Instance: `CompromisedEC2`, `MaliciousEC2`
  - S3 Bucket: `threat-list-[your-unique-id]`
  - IAM Role: `LambdaSecurityRole`
  - Lambda Function: `IsolateInstance`
  - EventBridge Rule: `GuardDutyToLambdaRule`
  - SNS Topic: `GuardDutyNotifications`

- **Valid Email Address:**  
  To receive notifications from Amazon SNS, you must have an email address that can receive messages and confirm subscriptions.

- **Check IAM Permissions:**  
  Ensure the user/role you are using has permissions to create and modify the above-mentioned services. If using an IAM user, verify the attached policies.

> 📌 Note: Avoid using the root account for deployment — instead, use an IAM user with appropriate permissions.
