---
title: "Create IAM Role"
date: 2025-06-18
weight: 2 
chapter: false
pre: " <b> 2.2 </b> "
---

### Create IAM Role

In this step, we will create an IAM Role.  
This IAM Role will be assigned the **AmazonSSMManagedInstanceCore** policy, which allows EC2 instances to communicate with AWS Systems Manager Session Manager.

1. Go to the [IAM Management Console](https://console.aws.amazon.com/iamv2/)  
2. In the left navigation pane, click **Roles**.  

![role](/000058-SessionManager/images/2.prerequisite/1.png)

3. Click **Create role**.  

![role1](/000058-SessionManager/images/2.prerequisite/2.png)

4. Select **AWS service** and then select **Lambda**.  
  + Click **Next**.  

![role1](/000058-SessionManager/images/2.prerequisite/image2.2.3.png)

5. Attach permissions for Lambda.  
  + In the search box, find and select the following policies:
      - `AmazonEC2FullAccess`  
      - `AWSLambda_FullAccess`  
      - `AWSLambdaBasicExecutionRole`  
      - `CloudWatchEventsFullAccess`  
      - `AmazonDynamoDBFullAccess`  
  + Click to select each policy:
      - **AmazonEC2FullAccess**  
      - **AWSLambda_FullAccess**  
      - **AWSLambdaBasicExecutionRole**  
      - **CloudWatchEventsFullAccess**  
      - **AmazonDynamoDBFullAccess**  
  + Click **Next**.  
  + Then click **Next** again.  

![createpolicy](/000058-SessionManager/images/2.prerequisite/4.png)  
![createpolicy](/000058-SessionManager/images/2.prerequisite/5.png)  
![createpolicy](/000058-SessionManager/images/2.prerequisite/7.png)  
![createpolicy](/000058-SessionManager/images/2.prerequisite/8.png)  
![createpolicy](/000058-SessionManager/images/2.prerequisite/6.png)  
![createpolicy](/000058-SessionManager/images/2.prerequisite/image2.2.6.png)

6. Set a name for the role:  
  - **Role name:** `aird_IAM`  
  - **Description:** `Allows Lambda functions to call AWS services on your behalf.`  

Then click **Next**.

![create role step 3](/000058-SessionManager/images/2.prerequisite/image2.2.7.png)

7. **Review and create the role**  
  - Double-check the attached policies.  
  - Click **Create role** to complete.  

![create role final confirm](/000058-SessionManager/images/2.prerequisite/image2.2.8.png)

8. Role successfully created:  
  - The role will appear in the IAM Roles list.  
  - Trusted entity: `lambda.amazonaws.com`  

![role created success](/000058-SessionManager/images/2.prerequisite/image2.2.9.png)
