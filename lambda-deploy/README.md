# 💻 Deploy and Configure AWS Lambda Functions

## 📝 Overview
Deploy and configure an AWS Lambda based serverless computing solution. The Lambda function generates a sales analysis report by pulling data from a database and emailing the results daily. The database connection information is stored in Parameter Store, a capability of AWS Systems Manager. The database runs on an Amazon EC2 instance configured with a LAMP stack (Linux, Apache, MySQL, PHP).

---

## 🔧 Tools & Technologies
* **AWS Lambda**
* **AWS CLI**
* **Amazon SNS** 
* **AWS IAM**
* **Amazon CloudWatch**
  
---

## 🚀 Steps
**1. Observed the IAM role settings**
* Observed the salesAnalysisReport IAM role settings

**2. Creating a Lambda layer and a data extractor Lambda function**
* Created a Lambda Layer
* Created a data extractor Lambda function
* Added the Lambda layer to the function
* Imported the code for the data extractor Lambda function
* Configured network settings for the function

**3. Tested the data extractor Lambda function**
* Launched a test of the Lambda function
* Troubleshoot the data extractor Lambda function
* Analyzed and corrected the Lambda function
* Performed a test run with sample data and verified results

**4. Configured notifications**
* Created an SNS topic
* Subscribed to the SNS topic

**5. Created the salesAnalysisReport Lambda function**
* Connected to the CLI Host instance
* Configured the AWS CLI
* Created the salesAnalysisReport Lambda function using the AWS CLI
* Configured the salesAnalysisReport Lambda function
* Tested the salesAnalysisReport Lambda function
* Added a trigger to the salesAnalysisReport Lambda function

## ✅ Result 
* Recognized necessary IAM policy permissions to enable a Lambda function to other AWS resources
* Created a Lambda layer to satisfy an external library dependency
* Created Lambda functions that extract data from the database and send reports to users
* Deployed and tested a scheduled Lambda function that invokes another function
* Used CloudWatch logs to troubleshoot any issues running a Lambda function
