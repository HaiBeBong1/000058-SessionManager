---
title: "Clean Up Resources"
date: 2025-06-18
weight: 10
chapter: false
pre: "<b>10.</b>"
---

> After completing the workshop, you need to **clean up resources** to avoid incurring costs.

## 1 Select and terminate EC2 instances
- Go to [EC2 console](https://console.aws.amazon.com/ec2/v2/home) → **Instances**
- Tick **all instances** to delete
- **Instance state** → **Terminate (delete) instance**
![CleanUpResources](/000058-SessionManager/images/10-CleanUpResources/1.png)

## 2Confirm Instances deletion
- Check the Instance ID list, the **Termination protection** column must be *Disabled*
- Do not select **Skip OS shutdown** (unless an emergency shutdown is required)
- Click **Terminate** to permanently delete
![CleanUpResources](/000058-SessionManager/images/10-CleanUpResources/2.png)

## 3 Delete unused Security Groups
- **Security Groups** (left menu)
- Tick the group security groups to delete
- **Actions** → **Delete security groups**
![CleanUpResources](/000058-SessionManager/images/10-CleanUpResources/3.png)

## 4 Confirm delete Security Groups
- Enter **delete** in the confirmation box
- Click **Delete** to complete
![CleanUpResources](/000058-SessionManager/images/10-CleanUpResources/4.png)

## 5 Delete Key Pair
- Go to **Key Pairs**
- Tick the key pair to delete
- **Actions** → **Delete**
![CleanUpResources](/000058-SessionManager/images/10-CleanUpResources/5.png)

### 6 Confirm delete Key Pair
- Enter **delete** in the confirmation box
- Click **Delete**

![CleanUpResources](/000058-SessionManager/images/10-CleanUpResources/6.png)

## 7 Delete GuardDuty Findings
- Go to **GuardDuty** → **Findings**
- Tick all findings
- **Actions** → **Archive**
![CleanUpResources](/000058-SessionManager/images/10-CleanUpResources/7.png)

---

## 8 Delete Threat IP List in GuardDuty
- Go to **Lists**
- Select the list to delete
- **Actions** → **Delete**

![CleanUpResources](/000058-SessionManager/images/10-CleanUpResources/8.png)

## 9 Delete AWS Lambda function
- Go to **Lambda** → **Functions**
- Tick the function to delete
- **Actions** → **Delete**

![CleanUpResources](/000058-SessionManager/images/10-CleanUpResources/9.png)

## 10 Confirm Deleting Lambda
- Enter **confirm** in the confirmation box
- Click **Delete**

![CleanUpResources](/000058-SessionManager/images/10-CleanUpResources/10.png)

---

## 11 Delete S3 Bucket
- Go to **Amazon S3**
- Select the bucket to delete
- Click **Delete**
![CleanUpResources](/000058-SessionManager/images/10-CleanUpResources/11.png)

## 12 Confirm Deleting Bucket
- Enter the bucket name in the confirmation box
- Click **Delete bucket**

![CleanUpResources](/000058-SessionManager/images/10-CleanUpResources/12.png)

## 13 Delete SNS Topic
- Go to **Amazon SNS** → **Topics**
- Select the topic to delete
- Click **Delete**

![CleanUpResources](/000058-SessionManager/images/10-CleanUpResources/13.png)
## 14 Delete VPC
- Go to **Your VPCs**
- Tick the VPC to delete
- **Actions** → **Delete VPC**

![CleanUpResources](/000058-SessionManager/images/10-CleanUpResources/14.png)

## 15 Confirm VPC deletion
- Check the list of resources to be deleted (Internet Gateway, Route Table, Subnet…)
- Enter **delete** in the confirmation box
- Click **Delete** to complete

![CleanUpResources](/000058-SessionManager/images/10-CleanUpResources/15.png)

---

## 16 Delete Subnet
- Go to **Subnets**
- Tick the subnet to delete
- **Actions** → **Delete subnet**

![CleanUpResources](/000058-SessionManager/images/10-CleanUpResources/16.png)

## 17 Confirm Subnet deletion
- Enter **delete** in the confirmation box
- Click **Delete** to complete

![CleanUpResources](/000058-SessionManager/images/10-CleanUpResources/17.png)

---

## 18 Delete IAM Roles
- Go to **IAM** → **Roles**
- Tick the unused roles
- Click **Delete**

![CleanUpResources](/000058-SessionManager/images/10-CleanUpResources/18.png)

---

## 19 Delete DynamoDB Table
- Go to **DynamoDB** → **Tables**
- Tick the table to delete
- Click **Delete**

![CleanUpResources](/000058-SessionManager/images/10-CleanUpResources/19.png)