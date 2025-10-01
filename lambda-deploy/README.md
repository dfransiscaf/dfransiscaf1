# 💻 Deploy and Configure AWS Lambda Functions

## 📝 Overview
Deploy and configure an AWS Lambda based serverless computing solution. The Lambda function generates a sales analysis report by pulling data from a database and emailing the results daily. The database connection information is stored in Parameter Store, a capability of AWS Systems Manager. The database runs on an Amazon EC2 instance configured with a LAMP stack (Linux, Apache, MySQL, PHP).

---

## 🔧 Tools & Technologies
* **AWS Lambda**
* **AWS CLI**
* **Amazon SNS** 
* **AWS IAM**

---

## 🚀 Steps
**1. Observed the IAM role settings**
* Observed the salesAnalysisReport IAM role settings
![Observed IAM role](https://github.com/user-attachments/assets/0dcbc777-04f4-4b34-b65c-dfdc6a025a1a)

**2. Creating a Lambda layer and a data extractor Lambda function**
* Created a Lambda Layer
  ![Lambda layer](https://github.com/user-attachments/assets/78e5ab19-e13b-4549-8ee5-829f56892c45)
* Created a data extractor Lambda function
  ![Created data extractor](https://github.com/user-attachments/assets/b1ca959c-c778-40d7-ba4f-f6183db70df8)
* Added the Lambda layer to the function
  ![Added lambda layer](https://github.com/user-attachments/assets/32739bb7-b6fd-4d57-94d8-0d3d99063511)
* Imported the code for the data extractor Lambda function
  ![Impored the code](https://github.com/user-attachments/assets/6cedc3a9-4cba-47fb-ac2c-cee9cbc96f25)
* Configured network settings for the function
  ![Configured network](https://github.com/user-attachments/assets/34836226-1a64-433e-be5d-371f3b4a4658)

**3. Tested the data extractor Lambda function**
* Launched a test of the Lambda function
  ![Launched a test](https://github.com/user-attachments/assets/1f113ad7-ec61-4bc7-a8db-bacc23f55056)
* Troubleshoot the data extractor Lambda function
  ![Troubleshoot](https://github.com/user-attachments/assets/6e5bb36f-91fe-4f47-86a4-06ed003aa69d)
* Analyzed and corrected the Lambda function
  ![Analyzed](https://github.com/user-attachments/assets/5b7160b9-9b23-49e4-aeec-a19666cf8c6e)
* Performed a test run with sample data and verified results
```json
{
  "statusCode": 200,
  "body": [
    {
      "product_group_number": 1,
      "product_group_name": "Pastries",
      "product_id": 1,
      "product_name": "Croissant",
      "quantity": 5
    },
    {
      "product_group_number": 2,
      "product_group_name": "Drinks",
      "product_id": 8,
      "product_name": "Hot Chocolate",
      "quantity": 2
    }
  ]
}
```
  ![Test with sample data](https://github.com/user-attachments/assets/4cdc4096-0cd4-497a-8019-1d57691799aa)

**4. Configured notifications**
* Created an SNS topic
  ![Created SNS](https://github.com/user-attachments/assets/28eb40d9-9ae9-47dd-bec4-217471836fd7)
* Subscribed to the SNS topic
  ![Subscribed](https://github.com/user-attachments/assets/07d1bdbc-c1ff-49e3-8a7c-a96c4d7cceba)

**5. Created the salesAnalysisReport Lambda function**
* Created the salesAnalysisReport Lambda function using the AWS CLI
```bash
aws lambda create-function \
  --function-name salesAnalysisReport \
  --runtime python3.9 \
  --zip-file fileb://salesAnalysisReport-v2.zip \
  --handler salesAnalysisReport.lambda_handler \
  --region <region> \
  --role <salesAnalysisReportRoleARN>
```
  ![Created lambda function](https://github.com/user-attachments/assets/6f56c577-5854-4214-9b20-a575c6b70bf1)
* Configured the salesAnalysisReport Lambda function
  ![Configured](https://github.com/user-attachments/assets/b220a037-70c4-4d26-a28a-f87bccdf4a06)
* Tested the salesAnalysisReport Lambda function
  ![Tested](https://github.com/user-attachments/assets/5848cf88-60ae-4133-a858-7e7d05d5c950)
* Added a trigger to the salesAnalysisReport Lambda function
  ![Added trigger](https://github.com/user-attachments/assets/1e25b95b-2113-4273-9f5c-5485448c7bbb)

## ✅ Result 
* Configured IAM policies to enable Lambda functions to access required AWS resources
* Created a Lambda layer to satisfy an external library dependency
* Created Lambda functions that extract data from the database and send reports to users
* Deployed and tested a scheduled Lambda function that invokes another function
* Used CloudWatch logs to troubleshoot any issues running a Lambda function
