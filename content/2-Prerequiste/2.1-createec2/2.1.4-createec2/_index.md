---
title: "Create EC2 Instance"
date: 2025-06-18
weight: 4
chapter: false
pre: " <b> 2.1.4 </b> "
---

1. Access the [EC2 management console](https://console.aws.amazon.com/ec2/v2/home)  
  + Click **Instances**.  
  + Click **Launch instances**.

![EC2](/images/2.prerequisite/image2.2.36.png)

2. In the Instance configuration  
  + Set **Name and tags**: enter **EC2**  
  + Set **Number of instances**: **2**  
  + Select **Quick Start**  
  + Choose **Amazon Linux 2**  
  + Select the appropriate AMI version

![EC2](/images/2.prerequisite/image2.2.37.png)

3. Configure Instance and Key Pair  
  + Select **Instance type**: **t2.micro**  
  + Click **Create new key pair**

![EC2](/images/2.prerequisite/image2.2.38.png)

4. Create a new Key Pair  
  + **Key pair name**: enter **kpair**  
  + **Key pair type**: select **RSA**  
  + **Private key format**: select **.pem**  
  + Click **Create key pair**

![EC2](/images/2.prerequisite/image2.2.39.png)

5. Configure Network Settings  
  + **VPC - required**: select **vpc-0bed0339b78a7b96e (security-workshop-vpc)**  
  + **Subnet**: select **Public-Subnet**  
  + **Auto-assign public IP**: select **Enable**  
  + **Security Group**: select **Public subnet - SG**  
  + Click **Launch instance**

![EC2](/images/2.prerequisite/11.png)

6. Finalize setup  
  + Rename the two instances to **MalC2** and **Compromised_EC**

![EC2](/images/2.prerequisite/image2.2.41.png)
