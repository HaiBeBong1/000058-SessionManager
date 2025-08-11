---
title: "Create Public Subnet"
date: 2025-06-18
weight: 2
chapter: false
pre: " <b> 2.1.2 </b> "
---

#### Create Public Subnet

1. Click **Subnets**.  
  + Click **Create subnet**.

![VPC](/images/2.prerequisite/image2.2.12.png)

2. On the **Create subnet** page:  
  + In **VPC ID**, select **security-workshop-vpc**.  
  + In **Subnet name**, enter **Public-Subnet**.  
  + In **Availability Zone**, choose the first availability zone.  
  + In **IPv4 CIDR block**, enter **10.10.1.0/24**.  
  + Click **Create subnet**.  

![VPC](/images/2.prerequisite/image2.2.13.png)

3. Scroll to the bottom of the page, click **Create subnet**.

4. Select **Lab Public Subnet**.  
  + Click **Actions**.  
  + Click **Edit subnet settings**.  

![VPC](/images/2.prerequisite/image2.2.14.png)

5. Select **Enable auto-assign public IPv4 address**.  
  + Click **Save**.  

![VPC](/images/2.prerequisite/image2.2.15.png)

6. Click **Internet Gateways**.  
  + Click **Create internet gateway**.  

![VPC](/images/2.prerequisite/image2.2.16.png)

7. On the **Create internet gateway** page:  
  + In **Name tag**, enter **igw-workshop**.  
  + Click **Create internet gateway**.  

![VPC](/images/2.prerequisite/image2.2.17.png)

8. After creation, click **Actions**.  
  + Click **Attach to VPC**.  

![VPC](/images/2.prerequisite/image2.2.18.png)

9. On the **Attach to VPC** page:  
  + In **Available VPCs**, select **security-workshop-vpc**.  
  + Click **Attach internet gateway**.  
  + Verify that the attachment was successful as shown below.  

![VPC](/images/2.prerequisite/image2.2.19.png)

10. Next, we will create a custom route table and associate it with **Lab Public Subnet**.  
  + Click **Route Tables**.  
  + Click **Create route table**.  

![VPC](/images/2.prerequisite/image2.2.20.png)

11. On the **Create route table** page:  
  + In **Name**, enter **rtb-public-subnet**.  
  + In **VPC**, select **security-workshop-vpc**.  
  + Click **Create route table**.  

![VPC](/images/2.prerequisite/image2.2.21.png)

12. After successfully creating the route table:  
  + Click **Edit routes**.  

![VPC](/images/2.prerequisite/image2.2.22.png)

13. On the **Edit routes** page:  
  + Click **Add route**.  
  + In **Destination**, enter `0.0.0.0/0`.  
  + In **Target**, select **Internet Gateway** and then choose **Lab IGW**.  
  + Click **Save changes**.  

![VPC](/images/2.prerequisite/image2.2.23.png)

14. Click the **Subnet associations** tab.  
  + Click **Edit subnet associations** to associate the custom route table with **Public-Subnet**.  

![VPC](/images/2.prerequisite/image2.2.24.png)

15. On the **Edit subnet associations** page:  
  + Select **Lab Public Subnet**.  
  + Click **Save associations**.  

![VPC](/images/2.prerequisite/image2.2.25.png)

16. Verify that the route table is associated with **Public-Subnet** and that the internet route is pointing to the Internet Gateway as shown below.  

![VPC](/images/2.prerequisite/image2.2.26.png)
