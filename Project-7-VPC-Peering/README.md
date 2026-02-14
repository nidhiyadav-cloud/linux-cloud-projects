# 7️⃣ VPC Peering Implementation

## 📌 Project Overview

This project demonstrates cross-VPC communication using AWS VPC Peering. Two custom VPCs were created with non-overlapping CIDR blocks and connected using a VPC Peering connection. Route tables were updated to enable private communication between EC2 instances.

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

## 🛠 Implementation Steps

### Step 1: Create VPC 1
- CIDR: 10.0.0.0/16
- Create subnet: 10.0.1.0/24
- Attach Internet Gateway

### Step 2: Create VPC 2
- CIDR: 192.168.0.0/16
- Create subnet: 192.168.1.0/24
- Attach Internet Gateway

### Step 3: Launch EC2 Instances
- Deploy one EC2 in each VPC
- Allow ICMP in Security Group
- Note private IP addresses

### Step 4: Create VPC Peering Connection
- Go to VPC → Peering Connections
- Select both VPCs
- Accept peering request

### Step 5: Update Route Tables

VPC 1 Route Table:
Destination → 192.168.0.0/16  
Target → Peering Connection

VPC 2 Route Table:
Destination → 10.0.0.0/16  
Target → Peering Connection

### Step 6: Verify Connectivity
SSH into EC2 of VPC 1 and ping private IP of EC2 in VPC 2.

ping <private-ip>

---

## 🔍 Key Learning

- Non-overlapping CIDR requirement
- VPC Peering is non-transitive
- Manual route table configuration required
- Direct private communication between VPCs

---

## 📸 Screenshots

(Add screenshots inside screenshots folder)

