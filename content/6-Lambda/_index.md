---
title : "Amazon Lambda"
weight : 6
chapter : false
pre : " <b> 6. </b> "
---

#### Create and Deploy a Lambda Function **aird_lambda**

1. **Create a Lambda Function**

- Go to [AWS Lambda Console](https://console.aws.amazon.com/lambda/).

- Click **Create a function**.

![Lambda](/000058-SessionManager/images/6.Lambda/1.png)

2. **Basic Configuration for Lambda**

- **Function name**: `aird_lambda`

- **Runtime**: Select `Python 3.13`

- Keep the default settings, then click **Create function**.

![Lambda](/000058-SessionManager/images/6.Lambda/2.png)

3. **Confirm Lambda function has been created**
- The interface displays the `aird_lambda` function with the status ready to configure and add triggers.
![Lambda](/000058-SessionManager/images/6.Lambda/3.png)

4. **Write source code for Lambda** 
- Open the **Code** tab → Add the file content `lambda_function.py` as follows:

```python
import boto3
import json
from botocore.exceptions import ClientError

# Initialize the EC2 client
ec2 = boto3.client('ec2')

def lambda_handler(event, context): 
try: 
# Log the incoming event to see its structure 
print(f"Received event: {json.dumps(event)}") 

# Extract instance ID from the event details 
if 'detail' in event and 'resource' in event['detail'] and 'instanceDetails' in event['detail']['resource']: 
instance_id = event['detail']['resource']['instanceDetails']['instanceId'] 
else: 
# Return an error if the event structure is unexpected 
return { 
'statusCode': 400, 
'body': json.dumps("Error: Event structure is not as expected.") 
} 

# Isolate the instance by modifying its security group 
response_sg = ec2.modify_instance_attribute( 
InstanceId=instance_id, 
Groups=['sg-01234abcd5678efgh'] # Replace with IsolatedSecurityGroup ID 
) 
print(f"Instance {instance_id} isolated: {response_sg}") 

# Stop the compromised instance 
response_stop = ec2.stop_instances( 
InstanceIds=[instance_id] 
) 
print(f"Instance {instance_id} stopped: {response_stop}") 

return { 
'statusCode': 200, 
'body': json.dumps(f"Instance {instance_id} successfully isolated and stopped.") 
} 

except ClientError as e: 
print(f"Error occurred: {e}") 
return { 
'statusCode': 500, 
'body': json.dumps(f"Error: {str(e)}") 
}
```
![Lambda](/000058-SessionManager/images/6.Lambda/4.png)



5. **Deploy code** 
- Click **Deploy** to save and apply the new code.
![Lambda](/000058-SessionManager/images/6.Lambda/5.png)

6. **Edit Lambda Configuration**

- Go to **Configuration** → **Edit**.

- Select **Existing role** as `aird_IAM`.

- Click **Save** to save the changes.

![Lambda](/000058-SessionManager/images/6.Lambda/6.png)
![Lambda](/000058-SessionManager/images/6.Lambda/7.png)

> Add environment variables so that the Lambda function can access DynamoDB table information and Security Group.

7. Open Lambda configuration

- Go to **Lambda** → Select function **aird_lambda**
- Select tab **Configuration**
- Select **Environment variables**
- Click **Edit**

![LambdaEnv](/000058-SessionManager/images/6.Lambda/10.png)

8. Add new environment variable

- Click **Add environment variable**

![LambdaEnv](/000058-SessionManager/images/6.Lambda/11.png)

9. Enter environment variable information

- Key: `TABLE_NAME` → Value: `CompromisedInstances`
- Key: `ISOLATED_SG_ID` → Value: ID of isolated Security Group (eg: `sg-00a6505c1ce061286`)
- You can add more variables if needed
- Click **Save** to save

![LambdaEnv](/000058-SessionManager/images/6.Lambda/12.png)

10. Get the saved environment variables
- Check the list of **Environment variables** showing all the keys and values just created

![LambdaEnv](/000058-SessionManager/images/6.Lambda/13.png)

11. **Test Lambda**
- Create a new test event, name it `test` and enter sample JSON data.
- Click **Save** to run the test.
![Lambda](/000058-SessionManager/images/6.Lambda/8.png)

12. **View log output**

- The log shows the event received and the processing steps.

![Lambda](/000058-SessionManager/images/6.Lambda/9.png)