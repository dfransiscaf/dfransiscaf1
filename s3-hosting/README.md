# ☁️ Hosting on Amazon S3 with Notifications

## 📝 Overview

Created and configured an **Amazon S3 bucket** to share images with an external user at a media company (`mediacouser`) who has been hired to provide pictures of the products that the café sells. The S3 bucket is configured to **automatically send an email notification** to the administrator whenever the bucket contents are modified.  

## 🔧 Tools & Technologies

* **Amazon S3** 
* **Amazon SNS** 
* **AWS IAM** 
* **AWS CLI** 

## 🚀 Steps

**1. Connected to the CLI Host EC2 instance and configured the AWS CLI**

   * Connected to an EC2 instance (CLI Host).
   * Configured AWS CLI with `aws configure` using **mediacouser** credentials.
     ![Set up CLI Host](https://github.com/user-attachments/assets/4eb5cd3b-92ac-4608-a363-13bd770610f2)

**2. Created and initialized the S3 share bucket**

   * Created a bucket (`cafe-247427`) to store product images.
   * Organized objects under `images/` prefix.
     ![Create S3 Bucket](https://github.com/user-attachments/assets/302e2789-de8a-4f25-a684-ae7a68d7b848)
     
**3. Reviewed and Tested the IAM group and user permissions**

   * Checked IAM group *mediaco* and user *mediacouser*.
   * Verified that mediacouser could **upload** and **delete** objects but could **not change bucket permissions**.
     ![Review & Testing IAM](https://github.com/user-attachments/assets/33022196-d493-44fb-9e5b-2f1966469e4c)
     
**4. Configured event notifications on the S3 share bucket**

   * Created an SNS topic `s3NotificationTopic`.
   * Subscribed admin email to receive notifications.
   * Added an event notification configuration to the S3 bucket.
     ![Configure Event Notifications](https://github.com/user-attachments/assets/546a178f-54ae-43af-bf85-45aacf235a77)
     
**5. Tested the S3 share bucket event notifications**

   * **Upload (PUT)** → uploaded `Caramel-Delight.jpg`

     ```bash
     aws s3api put-object --bucket <cafe-247427> --key images/Caramel-Delight.jpg --body ~/new-images/Caramel-Delight.jpg
     ```
     
     ✅ Email received: *ObjectCreated:Put*.

     * **Download (GET)** → downloaded `Donuts.jpg`

     ```bash
     aws s3api get-object --bucket <cafe-247427> --key images/Donuts.jpg Donuts.jpg
     ```

     ❌ Email not received: *Expected (notifications only for PUT/DELETE)*.

   * **Delete (REMOVE)** → deleted `Strawberry-Tarts.jpg`

     ```bash
     aws s3api delete-object --bucket <cafe-247427> --key images/Strawberry-Tarts.jpg
     ```

     ✅ Email received: *ObjectRemoved:Delete*.

   * **Unauthorized Action (FAIL)** → tried to set public ACL

     ```bash
     aws s3api put-object-acl --bucket <cafe-247427> --key images/Donuts.jpg --acl public-read
     ```

     ❌ Response: *AccessDenied*.

---

## ✅ Result

* Used the s3api and s3 AWS CLI commands to create and configure an S3 bucket
*	Verified write permissions to a user on an S3 bucket
*	Configured event notification on an S3 bucket
