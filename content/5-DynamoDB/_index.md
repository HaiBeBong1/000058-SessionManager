---
title: "Amazon DynamoDB"
date: 2025-06-18
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

> Create a DynamoDB table to store information about compromised EC2 instances.

1. Access DynamoDB  
   - Go to the [DynamoDB console](https://console.aws.amazon.com/dynamodb/home)  
   - Click **Create table**

![DynamoDB](/000058-SessionManager/images/5.DynamoDB/1.png)

2. Enter table details  
   - **Table name**: `CompromisedInstances`  
   - **Partition key**: `InstanceId` (String)  
   - **Sort key**: `Timestamp` (String)  
   - Select **Default settings**

![DynamoDB](/000058-SessionManager/images/5.DynamoDB/2.png)

3. Complete table creation  
   - Scroll down and click **Create table**

![DynamoDB](/000058-SessionManager/images/5.DynamoDB/3.png)

4. Confirm the table is successfully created  
   - Verify the table status is **Active**  
   - The table shows correct `Partition key` and `Sort key`

![DynamoDB](/000058-SessionManager/images/5.DynamoDB/4.png)
