# ☁️ Hosting & Notifications with Amazon S3

## 📝 Overview

Create and configure an **Amazon S3 bucket** to share images with an external user at a media company (`mediacouser`) who has been hired to provide pictures of the products that the café sells. The S3 bucket is configured to **automatically send an email notification** to the administrator whenever the bucket contents are modified.  

## 🔧 Tools & Technologies

* **Amazon S3** 
* **Amazon SNS** 
* **AWS IAM** 
* **AWS CLI** 

## 🚀 Steps

1. **Connecting to the CLI Host EC2 instance and configuring the AWS CLI**

   * Connected to an EC2 instance (CLI Host).
   * Configured AWS CLI with `aws configure` using **mediacouser** credentials.

2. **Creating and initializing the S3 share bucket**

   * Created a bucket (`cafe-247427`) to store product images.
   * Organized objects under `images/` prefix.

3. **Reviewing the IAM group and user permissions**

   * Checked IAM group *mediaco* and user *mediacouser*.
   * Verified that mediacouser could **upload** and **delete** objects but could **not change bucket permissions**.

4. **Configuring event notifications on the S3 share bucket**

   * Created an SNS topic `s3NotificationTopic`.
   * Subscribed admin email to receive notifications.
   * Added event notification on the bucket for **ObjectCreated** and **ObjectRemoved**.

5. **Testing the S3 share bucket event notifications**

   * **Upload (PUT)** → uploaded `Caramel-Delight.jpg`

     ```bash
     aws s3api put-object --bucket <cafe-247427> --key images/Caramel-Delight.jpg --body ~/new-images/Caramel-Delight.jpg
     ```
     
     ✅ Email received: *ObjectCreated:Put*.

     * **Download (GET)** → downloaded `Donuts.jpg`

     ```bash
     aws s3api get-object --bucket <cafe-247427> --key images/Donuts.jpg Donuts.jpg
     ```

     ❌ Email not received: *notifications only for PUT/DELETE*.

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
