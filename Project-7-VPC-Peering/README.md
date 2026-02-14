🏗 Project 7 : VPC Peering Implementation

## 📌 Project Overview

This project demonstrates cross-VPC communication using AWS VPC Peering. Two custom VPCs were created with non-overlapping CIDR blocks and connected using a VPC Peering connection. Route tables were updated to enable private communication between EC2 instances.

---

🛠️ AWS Services Used

1️⃣ Amazon VPC
2️⃣ VPC Peering Connection
3️⃣ Route Tables
4️⃣ Internet Gateway (IGW)
5️⃣ Amazon EC2
6️⃣ Security Groups

---

## 🏗 Architecture

- VPC 1: 10.0.0.0/16
- VPC 2: 192.168.0.0/16
- Public Subnet in each VPC
- One EC2 instance in each VPC
- VPC Peering Connection
- Route Table updates
- ICMP (Ping) verification

---

🏗️ Architecture Diagram

                         🌍 INTERNET
                              ▲
                              |
                    0.0.0.0/0 | Route
                              |
                     -----------------
                     |      IGW-1    |
                     -----------------
                              ▲
                              |
                    ---------------------
                    |   VPC-1           |
                    |   10.0.0.0/16     |
                    |                   |
                    |  EC2-1            |
                    |  10.0.1.70        |
                    ---------------------
                              |
                              | Route:
                              | 192.168.0.0/16 → pcx
                              ↓
               ===================================
                 🔗  VPC PEERING (pcx-037c64b1d348afffc)
               ===================================
                              ↑
                              | Route:
                              | 10.0.0.0/16 → pcx
                    ---------------------
                    |   VPC-2           |
                    |   192.168.0.0/16  |
                    |                   |
                    |  EC2-2            |
                    |  192.168.1.189    |
                    ---------------------
                              |
                              |
                     -----------------
                     |      IGW-2    |
                     -----------------
                              |
                              ▼
                         🌍 INTERNET

---

## 🛠 Implementation Steps

### Step 1: Create VPC 1 and VPC 2
- CIDR: 10.0.0.0/16 and 192.168.0.0/16
 📸 Screenshot: ![VPC](Screenshot 2026-02-14 212226.png)

### Step 2: Create subnet
- subnet: 10.0.1.0/24 and 192.168.1.0/24
📸 Screenshot: ![subnet](Screenshot 2026-02-14 212915.png)
  
### Step 3: Create Internet Gateway
 - Creating 2 igw for both vpc(vpc1 and vpc2)
 - Add IGW to route table of both VPCs
📸 Screenshot: ![IGW](Screenshot 2026-02-14 214331.png)
 
### Step 3: Launch EC2 Instances
- Deploy one EC2 in each VPC
- Allow ICMP in Security Group
- Note private IP addresses
📸 Screenshot: ![EC2 Instance](Screenshot 2026-02-14 202257.png)
  
### Step 4: Create VPC Peering Connection
- Go to VPC → Peering Connections
- Select both VPCs
- Accept peering request
📸 Screenshot: ![Peering] Screenshot 2026-02-14 212651.png

### Step 5: Update Route Tables
VPC 1 Route Table:
Destination → 192.168.0.0/16  
Target → Peering Connection
📸 Screenshot: ![Route Table VPC1](Screenshot 2026-02-14 212813.png)

VPC 2 Route Table:
Destination → 10.0.0.0/16  
Target → Peering Connection
📸 Screenshot: ![Route Table VPC2](Screenshot 2026-02-14 212835.png)

### Step 6: Verify Connectivity
SSH into EC2 of VPC 1 and ping private IP of EC2 in VPC 2.

ping <192.168.1.189>
📸 Screenshot: ![Ping Success](Screenshot 2026-02-14 202225.png)

---

🎤 Interview Explanation

In this project, I implemented VPC Peering between two VPCs to enable private communication between EC2 instances located in separate networks.

I created two VPCs with non-overlapping CIDR ranges. Each VPC had its own Internet Gateway for internet access.

I established a VPC Peering connection and updated the route tables in both VPCs to route traffic through the peering connection.

I configured security groups to allow ICMP traffic and verified connectivity by pinging private IP addresses between instances.

This project helped me understand AWS networking fundamentals including route tables, security groups, non-transitive routing, and private network communication.

---

🧠 Key Learnings

✅ VPC Isolation

By default, VPCs are isolated even if they have internet access.

✅ Peering Enables Private Communication

VPC Peering allows secure private IP communication.

✅ Non-Transitive Routing

Traffic cannot pass through one VPC to reach another resource (like Internet Gateway).

✅ Route Table Importance

Peering works only when both VPC route tables are updated.

✅ Security Group Controls Traffic

Even with correct routing, traffic fails if SG blocks it.

✅ Internet Gateway ≠ VPC-to-VPC Communication

---


