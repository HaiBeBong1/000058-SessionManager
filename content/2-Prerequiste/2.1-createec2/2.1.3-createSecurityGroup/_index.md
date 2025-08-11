---
title: "Create Security Group for Public and Isolated"
date: 2025-06-18
weight: 3
chapter: false
pre: " <b> 2.1.3 </b> "
---

#### Create Security Group

1. Access the [VPC management console](https://console.aws.amazon.com/vpc)  
  + Click **Security Group**.  
  + Click **Create security group**.

![SG](/images/2.prerequisite/image2.2.27.png)

2. Configure basic information  
  + **Security Group name**: Enter **Public subnet - SG**  
  + **Description**: Enter **Allow SSH and Ping for servers in public subnet**  
  + **VPC**: Select **security-workshop-vpc**

![SG](/images/2.prerequisite/image2.2.28.png)

3. Set up **Inbound Rules**  
  + Click **Add rule**  
  + Rule 1:  
      - Type: **SSH**  
      - Source: **My IP** (your public IPv4 address)  
  + Rule 2:  
      - Type: **All ICMP - IPv4**  
      - Source: **Anywhere** (allow ping from anywhere)

![SG](/images/2.prerequisite/image2.2.29.png)

4. Verify **Outbound Rules** and create Security Group  
  + Click **Add rule**  
  + Type: **All traffic**  
  + Destination: **Anywhere (0.0.0.0/0)**  
  + Click **Create security group**.

![SG](/images/2.prerequisite/image2.2.30.png)

5. Verify the created Security Group

![SG](/images/2.prerequisite/image2.2.31.png)

---

#### Create Isolated Security Group

1. Access the [VPC management console](https://console.aws.amazon.com/vpc)  
  + Click **Security Group**.  
  + Click **Create security group**.

![SG](/images/2.prerequisite/image2.2.32.png)

2. Configure basic information for the isolated Security Group  
  + **Security Group name**: Enter `sg-isolated`  
  + **Description**: Enter `Security Group to isolate compromised EC2`  
  + **VPC**: Select the same VPC used for the lab (e.g., `security-workshop-vpc`)

  > 🎯 This is the security group that will be assigned to EC2 instances detected as compromised — isolating them from the entire network.

![SG](/images/2.prerequisite/image2.2.33.png)

3. **Configure Inbound Rules**  
  + Click **Add rule**  
  + Rule 1:  
      - Type: **SSH**  
      - Source: **My IP** (your public IPv4 address)

4. **Outbound Rules**  
  + If the default rule exists (**All traffic → 0.0.0.0/0**), keep it.  
  + After creation, you will see `sg-isolated` in the list.  
  + You can use this Security Group with Lambda or EventBridge to automatically move compromised EC2 instances into isolation.  
  + Click **Create security group** to finish.

![SG](/images/2.prerequisite/image2.2.42.png)
