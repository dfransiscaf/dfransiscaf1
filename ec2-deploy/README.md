# Deploying a Web App on EC2

## 📌 Overview
This project demonstrates how to deploy a simple web application on **Amazon EC2**.

## ⚙️ Tools & Technologies
- AWS EC2  
- Linux  
- Security Groups  

## 🚀 Steps
## 1. Launching EC2 Instance
- **Step 1:** Naming EC2 instance  
- **Step 2:** Choosing an Amazon Machine Image (AMI)  
- **Step 3:** Choosing an instance type  
- **Step 4:** Configuring a key pair  
- **Step 5:** Configuring the network settings  
- **Step 6:** Adding storage  
- **Step 7:** Configuring advanced details  
- **Step 8:** Launching an EC2 instance  

## 2. Monitor EC2 Instance
- **Step 1:** Select the instance by checking the box and navigate to the *Status checks* tab  
- **Step 2:** Select the *Monitoring* tab  
- **Step 3:** In the Actions menu, select *Monitor and troubleshoot → Get Instance Screenshot*  

## 3. Update Security Group & Access the Web Server
- **Step 1:** Select the *Details* tab  
- **Step 2:** Copy the **Public IPv4 address**  
- **Step 3:** Open a new browser tab, paste the IP address, then press **Enter**  
- **Step 4:** Return to the EC2 Management Console tab and select **Security Groups**  
- **Step 5:** Select *Web Server security group* and open the **Inbound rules** tab  
- **Step 6:** Select **Edit inbound rules → Add rule** (Type: `HTTP`, Source: `Anywhere-IPv4`)  
- **Step 7:** Save rules, return to the web server and refresh the page 

## ✅ Result
Web app successfully deployed and accessible via Public IPv4
