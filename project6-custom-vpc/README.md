# Project 6: Custom VPC with Public & Private Subnets

## 🎯 Objective
To create a custom VPC with public and private subnets and deploy EC2 instances demonstrating network isolation and secure architecture.

---

## 🛠️ AWS Services Used
- VPC
- Subnets
- Internet Gateway
- Route Tables
- EC2
- Security Groups

---

## 🏗️ Architecture Diagram

              Internet
                  ↓
           Internet Gateway
                  ↓
             Custom VPC
        -----------------------
        |                     |
   Public Subnet        Private Subnet
   (10.0.1.0/24)        (10.0.2.0/24)
        |                     |
   EC2 Web Server        EC2 App Server
   (65.0.132.248)           (10.0.2.87)


---

## 🔹 Implementation Steps

### Step 1: Created Custom VPC
- CIDR: 10.0.0.0/16

📸 Screenshot:
![VPC](Screenshot 2026-02-14 014730.png)

---

### Step 2: Created Public & Private Subnets
- Public: 10.0.1.0/24
- Private: 10.0.2.0/24

📸 Screenshot:
![Subnets](screenshots/2-subnets.png)

---

### Step 3: Created and Attached Internet Gateway

📸 Screenshot:
![IGW](screenshots/3-igw.png)

---

### Step 4: Configured Route Table
- Added 0.0.0.0/0 route to Internet Gateway
- Associated with Public Subnet

📸 Screenshot:
![Route Table-private](Screenshot 2026-02-14 015116.png)

---

### Step 5: Launched EC2 Instances
- Public EC2 with public IP (Web server)
- Private EC2 without public IP

📸 Screenshot:
![Public EC2](Screenshot 2026-02-14 015350.png)

📸 Screenshot:
![Private EC2](Screenshot 2026-02-14 015452.png)

---

## 💬 Interview Explanation

"I designed a custom VPC with separate public and private subnets. The public subnet hosts a web server accessible via Internet Gateway, while the private subnet hosts an application server isolated from the internet. This demonstrates secure network design and understanding of AWS networking fundamentals."

---

## ✅ Key Learning
- CIDR block planning
- Subnet creation
- Route table configuration
- Internet Gateway setup
- Network isolation in AWS

