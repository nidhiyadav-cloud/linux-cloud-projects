# Project 6: Custom VPC with Public & Private Subnets

## 🎯 Objective
To create a custom VPC with public and private subnets and deploy EC2 instances demonstrating network isolation and secure architecture.

---

## 🛠️ AWS Services Used
- VPC
- Subnets
- Internet Gateway
- NAT Gateway
- Route Tables
- EC2
- Security Groups

---

## 🏗️ Architecture Diagram

                           Internet
                              │
                     ┌────────▼────────┐
                     │ Internet Gateway │
                     └────────┬────────┘
                              │
                      ┌───────▼────────┐
                      │   Custom VPC    │
                      │  10.0.0.0/16    │
                      └────────┬────────┘
            ───────────────────┼───────────────────
                               │
                 ┌─────────────▼─────────────┐
                 │        Public Subnet       │
                 │       10.0.1.0/24          │
                 │                             │
                 │  Bastion Host (EC2)        │
                 │  + Public IP               │
                 │                             │
                 │  NAT Gateway               │
                 └─────────────┬─────────────┘
                               │
                               │ (Private Route: 0.0.0.0/0 → NAT)
                 ┌─────────────▼─────────────┐
                 │        Private Subnet      │
                 │       10.0.2.0/24          │
                 │                             │
                 │  Private EC2 Instance      │
                 │  (No Public IP)            │
                 │                             │
                 │  ping 8.8.8.8              │
                 └─────────────────────────────┘



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
![Subnets](Screenshot 2026-02-14 001004.png)

---

### Step 3: Created and Attached Internet Gateway

📸 Screenshot:
![IGW](Screenshot 2026-02-14 001224.png)

---

### Step 4: Configured Route Table
- Added 0.0.0.0/0 route to Internet Gateway
- Associated with Public Subnet
- Added 0.0.0.0/0 route to NAT Gateway
- Associated with private subnet

📸 Screenshot:
![Route Table-private](Screenshot 2026-02-14 015116.png)
![Route Table-public](Screenshot 2026-02-14 001521.png)
---

### Step 5: Launched EC2 Instances
- Public EC2 with public IP (Web server)
- Private EC2 without public IP
- Made Bastion Host
- Ping 8.8.8.8 from private instance

📸 Screenshot:
![Public EC2](Screenshot 2026-02-14 015350.png)

📸 Screenshot:
![Private EC2](Screenshot 2026-02-14 015452.png)

📸 Screenshot:
![Ping 8.8.8.8](Screenshot 2026-02-14 013932.png)
---

## 💬 Interview Explanation

In this project, I created a custom VPC with public and private subnets to demonstrate secure network architecture.

A Bastion Host was deployed in the public subnet to securely access the private EC2 instance. The private instance does not have a public IP, ensuring network isolation.

To enable outbound internet access for the private instance, I configured a NAT Gateway and updated the route table accordingly. I verified connectivity by running `ping 8.8.8.8` from the private instance.

This project demonstrates VPC creation, subnet isolation, route table configuration, Bastion Host setup, and NAT Gateway implementation.


---

## 🔄 Traffic Flow Explanation

Public Instance Access:
Internet → Internet Gateway → Public Subnet → Bastion Host

Private Instance Outbound Access:
Private EC2 → Route Table (0.0.0.0/0) → NAT Gateway → Internet Gateway → Internet


## ✅ Key Learning
- Custom VPC creation and CIDR planning
- Public and private subnet architecture
- Internet Gateway configuration
- NAT Gateway setup for outbound internet access
- Bastion Host for secure access control
- Route table configuration and traffic flow understanding

This implementation reflects a secure and production-style AWS networking setup.

