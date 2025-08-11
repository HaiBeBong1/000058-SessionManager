---
title: "Results achieved"
date: 2025-06-18
weight: 9
chapter: false
pre: "<b>9.</b>"
---

## Results

1. **List EC2 instances**

+ Two EC2 instances are created under Security Group **Public subnet - SG**.
![result](/000058-SessionManager/images/9.result/1.png)
2. **Tick on Compromised_EC2**

+ Select instance **Compromised_EC2**, then click **Connect**.
![result](/000058-SessionManager/images/9.result/8.1.png)
3. **SSH connection**

+ Use the SSH command below to connect to EC2:

+ Click **Yes**

bash
ssh -i "kpair.pem" ec2-user@47.128.65.71

![result](/000058-SessionManager/images/9.result/5.1.png)
![result](/000058-SessionManager/images/9.result/6.1.png)
4. Check user & switch to root
+ use the following commands:
bash
whomi # mistype -> error "command not found"
whoami # correct: return 'ec2-user'
sudo su # switch to user 'root'
whoami # confirm: 'root'
nano payload.sh # create script

![result](/000058-SessionManager/images/8.result/7.1.png)
5.Script content
bash
#!/bin/bash
for j in {1..10}; do
sudo nmap -sT -Pn 13.229.210.16
done

+ Get the address of **MalC2** IPv4: 13.229.210.16
![result](/000058-SessionManager/images/9.result/9.1.png)
![result](/000058-SessionManager/images/9.result/10.1.png)

6. Save the payload.sh file:

+ Press Ctrl + O (Write Out)
+ Press Enter to confirm the file name (payload.sh)
+ Press Ctrl + X to exit nano

7. Run the command

bash
chmod +x payload.sh
./payload.sh

![result](/000058-SessionManager/images/9.result/20.png)

9. This result is consistent over multiple scans, proving that the current network configuration only allows SSH access and blocks all other services.

![result](/000058-SessionManager/images/9.result/11.png)

10. EC2 Status after Action
After determining **Compromised_EC2** is vulnerable to exploitation, this instance has been assigned to **Security Group “Sg-isolated”** to block all network connections.

- **MalC2**
- Status: **Running** (2/2 checks passed)

- **Compromised_EC2**
- Status: **Stopping** (stopping)

![result](/000058-SessionManager/images/9.result/12.png)

11. EC2 Isolation via Security Group
+ After determining **Compromised_EC2** is vulnerable to exploitation, this instance has been assigned to **Security Group “Sg-isolated”** to block all network connections.
![result](/000058-SessionManager/images/9.result/13.png)
+ This measure helps:
- **Prevent the risk from spreading** to other resources.
- **Preserve on-site data** to investigate the cause and method of attack.
12. Detection from AWS GuardDuty
AWS GuardDuty has recorded a **Recon:EC2/Portscan** event with a severity of **Medium** for instance i-02cc787dd11d0703f (**Compromised_EC2**).
![result](/000058-SessionManager/images/9.result/14.png)
13. GuardDuty Alert Details

Alert Details:

- **Finding ID**: 16cc49ab87e99a0d94f0d379281477d6
- **Type**: Recon:EC2/Portscan
- **Severity**: MEDIUM
- **Region**: ap-southeast-1
- **Detection Time**: 2025-10-08 16:36:53
- **Target Address**: 13.229.210.16
- **Resource**: i-02cc787dd11d0703f

![result](/000058-SessionManager/images/9.result/15.png)
![result](/000058-SessionManager/images/9.result/16.1.png)
14. AWS SNS has sent a confirmation message:
+ This indicates that the incident response process was successful: the EC2 was isolated from the network and stopped, preventing any further activity from this source.
![result](/000058-SessionManager/images/9.result/17.png)

15. AWS DynamoDB has saved
+ Click on **Table**
+ Click on **Compromisedlnstances**
![result](/000058-SessionManager/images/9.result/18.png)
![result](/000058-SessionManager/images/9.result/19.png)translate this paragraph to English for use in Hugo with no changes