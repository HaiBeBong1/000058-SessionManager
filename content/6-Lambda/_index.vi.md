---
title : "Amazon Lambda"
weight : 6 
chapter : false
pre : " <b> 6. </b> "
---


#### Tạo và triển khai hàm Lambda **aird_lambda**

1. **Tạo Lambda Function**  
   - Truy cập [AWS Lambda Console](https://console.aws.amazon.com/lambda/).  
   - Nhấn **Create a function**.  

![Lambda](/000058-SessionManager/images/6.Lambda/1.png)



2. **Cấu hình cơ bản cho Lambda**  
   - **Function name**: `aird_lambda`  
   - **Runtime**: Chọn `Python 3.13`  
   - Giữ nguyên các thiết lập mặc định, sau đó nhấn **Create function**.  

![Lambda](/000058-SessionManager/images/6.Lambda/2.png)



3. **Xác nhận hàm Lambda đã được tạo**  
    - Giao diện hiển thị hàm `aird_lambda` với trạng thái sẵn sàng cấu hình và thêm trigger.  
![Lambda](/000058-SessionManager/images/6.Lambda/3.png)

4. **Viết mã nguồn cho Lambda**  
    - Mở tab **Code** → Thêm nội dung file `lambda_function.py` như sau:  

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
            Groups=['sg-01234abcd5678efgh']  # Thay bằng IsolatedSecurityGroup ID
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



5. **Triển khai code**  
   - Nhấn **Deploy** để lưu và áp dụng code mới.  
![Lambda](/000058-SessionManager/images/6.Lambda/5.png)


6. **Chỉnh sửa cấu hình Lambda**  
   - Vào **Configuration** → **Edit**.  
   - Chọn **Existing role** là `aird_IAM`.    
   - Nhấn **Save** để lưu thay đổi.  
![Lambda](/000058-SessionManager/images/6.Lambda/6.png)
![Lambda](/000058-SessionManager/images/6.Lambda/7.png)




> Thêm các biến môi trường (Environment Variables) để Lambda function có thể truy cập thông tin bảng DynamoDB và Security Group.

7. Mở phần cấu hình Lambda
    - Vào **Lambda** → Chọn function **aird_lambda**  
    - Chọn tab **Configuration**  
    - Chọn **Environment variables**  
    - Click **Edit**

![LambdaEnv](/000058-SessionManager/images/6.Lambda/10.png)



8. Thêm biến môi trường mới
    - Click **Add environment variable**

![LambdaEnv](/000058-SessionManager/images/6.Lambda/11.png)


9. Nhập thông tin biến môi trường
    - Key: `TABLE_NAME` → Value: `CompromisedInstances`  
    - Key: `ISOLATED_SG_ID` → Value: ID của Security Group cô lập (ví dụ: `sg-00a6505c1ce061286`)  
    - Có thể thêm biến khác nếu cần  
    - Click **Save** để lưu

![LambdaEnv](/000058-SessionManager/images/6.Lambda/12.png)


10. nhận biến môi trường đã được lưu
    - Kiểm tra danh sách **Environment variables** hiển thị đầy đủ các key và value vừa tạo

![LambdaEnv](/000058-SessionManager/images/6.Lambda/13.png)


11. **Kiểm tra Lambda**  
   - Tạo test event mới, đặt tên `test` và nhập dữ liệu JSON mẫu.  
   - Nhấn **Save** để chạy thử.  
![Lambda](/000058-SessionManager/images/6.Lambda/8.png)

12. **Xem kết quả log**  
   - Log hiển thị sự kiện nhận được và các bước xử lý.  

![Lambda](/000058-SessionManager/images/6.Lambda/9.png)


