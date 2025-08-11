---
title: "Create SNS"
weight: 1
chapter: false
pre: "<b>8.1. </b>"
draft: false
---

#### Create Amazon SNS Topic **Automated_idr_SNS** and subscribe an email address to receive notifications

1. Go to the [Amazon SNS Management Console](https://console.aws.amazon.com/sns/v3/home).  
   + Click **Create topic**.  
   + Enter **Automated_idr_SNS** as the topic name.  
![SNS](/images/8.SNS/1.png)

2. Configure the topic.  
   + **Type**: select **Standard**.  
   + **Name**: enter `Automated_idr_SNS`.  
   + **Display name**: enter `SNS Topic`.  
   + Click **Create topic**.  

![SNS](/images/8.SNS/2.png)  
![SNS](/images/8.SNS/3.png)  

---

#### Create a Subscription for Topic **Automated_idr_SNS**

3. On the topic details page, select **Create subscription**.  
![SNS](/images/8.SNS/4.png)

4. Configure the subscription.  
   + **Protocol**: select `Email`.  
   + **Endpoint**: enter *your email address*.  
   + Click **Create subscription**.  
![SNS](/images/8.SNS/5.png)

5. After creation, the subscription status will be **Pending confirmation**.  
![SNS](/images/8.SNS/6.png)

6. Open the confirmation email from AWS Notification and click **Confirm subscription**.  
![SNS](/images/8.SNS/7.png)

7. Once confirmed, the system will display **Subscription confirmed!**.  
![SNS](/images/8.SNS/8.png)
