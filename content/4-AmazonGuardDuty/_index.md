---
title: "Amazon GuardDuty"
date: 2025-06-18
weight: 4
chapter: false
pre: " <b> 4. </b> "
---

#### Enable Amazon GuardDuty and configure Threat IP List

1. **Enable GuardDuty**  
   - Go to the [AWS GuardDuty Console](https://console.aws.amazon.com/guardduty/).  
   - Select **Amazon GuardDuty - all features** and click **Get started** to activate the service.  
![GuardDuty](/images/4.GuardDuty/1.png)

2. **Access Lists section**  
   - After successful activation, from the left menu, select **Settings** → **Lists**.  

![GuardDuty](/images/4.GuardDuty/2.png)

3. **Add Threat IP List**  
   - In the **Threat IP list** section, click **Add a threat ip list**.  

![GuardDuty](/images/4.GuardDuty/3.png)

4. **Enter Threat IP List information**  
   - **List name**: `ThreatList`  
   - **Location**: `https://threatlists3.s3.ap-southeast-1.amazonaws.com/ThreatList.txt`  
   - **List format**: `Plaintext`  
   - Click **Add list** to save.  

![GuardDuty](/images/4.GuardDuty/4.png)

5. **Activate Threat IP List**  
   - After adding successfully, select the newly created list → **Actions** → **Activate** to enable it.  

![GuardDuty](/images/4.GuardDuty/5.png)
