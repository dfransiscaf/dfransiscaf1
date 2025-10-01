# Deploying a Web App on EC2

## 📝 Overview
This project demonstrates how to deploy a simple web application on **Amazon EC2**.

## 🔧 Tools & Technologies
- Amazon EC2  
- Amazon Machine Image (AMI)    
- VPC & Security Groups  
- Elastic Block Store (EBS)  
- Amazon Linux 2

## 🚀 Steps
## 1. Launching EC2 Instance
- **Step 1:** Naming EC2 instance
![Naming EC2](https://github.com/user-attachments/assets/cb417e50-f9ca-479b-8dce-fc41f7747d84)
- **Step 2:** Choosing an Amazon Machine Image (AMI)
![Choosing AMI](https://github.com/user-attachments/assets/db40a6c4-5abc-4cdf-b3a2-a38870300875)
- **Step 3:** Choosing an instance type
![Choosing Instance Type](https://github.com/user-attachments/assets/4c263928-aac0-45de-8295-0df5dbbc2c52)
- **Step 4:** Configuring a key pair
![Key Pair](https://github.com/user-attachments/assets/39e5c6a3-b2d9-4481-9382-4c4b67d2566d)
- **Step 5:** Configuring the network settings
![Network Setting](https://github.com/user-attachments/assets/b4eda933-0c2d-4b31-bf32-8b0ebba20a02)
- **Step 6:** Adding storage
![Adding Storage](https://github.com/user-attachments/assets/d4a85d38-4011-494f-8c73-903773fa22ba)
- **Step 7:** Configuring advanced details
![Advanced Details](https://github.com/user-attachments/assets/2e2c79ef-0e0f-4b0a-a6e1-b11cbb674678)
- **Step 8:** Launching an EC2 instance
![Launch EC2](https://github.com/user-attachments/assets/81bdd610-a312-4b86-ab5c-a76ca9c7ad0c)

## 2. Monitor EC2 Instance
- **Step 1:** Select the instance by checking the box and navigate to the *Status checks* tab  
- **Step 2:** Select the *Monitoring* tab  
- **Step 3:** In the Actions menu, select *Monitor and troubleshoot → Get Instance Screenshot*
![Monitor EC2 Instance](https://github.com/user-attachments/assets/342c72e1-581c-4d80-bf87-6a324781d60e)

## 3. Update Security Group & Access the Web Server
- **Step 1:** Select the *Details* tab  
- **Step 2:** Copy the **Public IPv4 address**  
- **Step 3:** Open a new browser tab, paste the IP address, then press **Enter**  
- **Step 4:** Return to the EC2 Management Console tab and select **Security Groups**  
- **Step 5:** Select *Web Server security group* and open the **Inbound rules** tab  
- **Step 6:** Select **Edit inbound rules → Add rule** (Type: `HTTP`, Source: `Anywhere-IPv4`)
![Add Security Group](https://github.com/user-attachments/assets/77b623b0-bc2f-4da5-a022-8fb067431448)
- **Step 7:** Save rules, return to the web server and refresh the page
![Web App Launched](https://github.com/user-attachments/assets/07c2e023-0091-4fbb-b173-42db472c670f)

## ✅ Result
Web app successfully deployed and accessible via Public IPv4
