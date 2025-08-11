---
title: "Amazon Lambda"
weight: 6
chapter: false
pre: " <b> 6. </b> "
---

#### Create and deploy Lambda function **aird_lambda**

1. **Create Lambda Function**  
   - Go to the [AWS Lambda Console](https://console.aws.amazon.com/lambda/).  
   - Click **Create a function**.  

![Lambda](/images/6.Lambda/1.png)

2. **Basic configuration for Lambda**  
   - **Function name**: `aird_lambda`  
   - **Runtime**: Select `Python 3.13`  
   - Keep default settings, then click **Create function**.  

![Lambda](/images/6.Lambda/2.png)

3. **Confirm Lambda function created**  
   - The console shows the `aird_lambda` function ready for configuration and adding triggers.  

![Lambda](/images/6.Lambda/3.png)

4. **Write Lambda source code**  
   - Open the **Code** tab → Add the following content to `lambda_function.py`:  

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
            Groups=['sg-01234abcd5678efgh']  # Replace with your IsolatedSecurityGroup ID
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
