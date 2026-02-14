🚀 Project 8 – AWS Transit Gateway (Multi-VPC Connectivity)

🧰 AWS Services Used

Amazon VPC – Created 3 VPCs with non-overlapping CIDR blocks

Amazon EC2 – Launched instances in each VPC for testing

AWS Transit Gateway (TGW) – Central routing hub

Transit Gateway Attachments – Attached each VPC to TGW

Route Tables (VPC & TGW) – Configured routing

Security Groups – Allowed ICMP & SSH

Internet Gateway (Optional for Internet access)

---

🏗 Architecture Overview

We will create:

1. VPC-1 (10.0.0.0/16)

2. VPC-2 (192.168.0.0/16)

3. VPC-3 (172.16.0.0/16)

4. 1 Transit Gateway

5. EC2 in each VPC

6. Route tables configuration

---

📊 Architecture Diagram

           VPC-1 (10.0.0.0/16)
                |
                |
                |
           -------------
           |  Transit  |
           |  Gateway  |
           -------------
             /      \
            /        \
           /          \
VPC-2 (192.168.0.0/16)   VPC-3 (172.16.0.0/16)

🔥 TGW works like central router.

---

🛠 Implementation

🟢 Step 1: Created 3 VPCs

VPC-1 → 10.0.0.0/16

VPC-2 → 192.168.0.0/16

default-VPC → 172.31.0.0/16

📸 Screenshot: ![VPC Creation](Screenshot 2026-02-15 001053.png)

🟢 Step 2:  Create Internet Gateway

 1. Creating 3 igw for each vpc(vpc1 , vpc2 and vpc3)

 2. Add IGW to route table of both VPCs
📸 Screenshot: ![IGW](Screenshot 2026-02-15 001233.png)

🟢 Step 3: Launched EC2 in Each VPC

1. Enabled ICMP in Security Group

2. Used private IP for testing

 📸 Screenshot: ![EC2 Instances](Screenshot 2026-02-15 001342.png)

🟢 Step 4: Created Transit Gateway

1. Created TGW

2. Status: Available
   
📸 Screenshot: ![Transit Gateway Creation](Screenshot 2026-02-15 001419.png)

🟢 Step 5: Created TGW Attachments

 1. Attached each VPC to Transit Gateway

 2. Status: Available

📸 Screenshot: ![TGW Attachments](Screenshot 2026-02-15 001459.png)

🟢 Step 6: Updated Route Tables

In each VPC route table:

 rtb-vpc-1: 
 192.168.0.0/16 → Transit Gateway
 172.16.0.0/16 → Transit Gateway

 📸 Screenshot: ![Route Table](Screenshot 2026-02-15 001535.png)
 
 rtb-vpc-2:
 10.0.0.0/16  → Transit Gateway
 172.31.0.0/16 → Transit Gateway

📸 Screenshot: ![Route Table](Screenshot 2026-02-15 001637.png)
 
 rtb-default:
 192.168.0.0/16  → Transit Gateway
 10.0.0.0/16  → Transit Gateway

 📸 Screenshot: ![Route Tables](Screenshot 2026-02-15 001708.png)
 
 🟢 Step 7: Verify Connectivity
 
 1. SSH into EC2 of VPC 1 and ping private IP of EC2 in VPC 2 and EC2 in default-VPC.

  📸 Screenshot: ![Ping Success <192.168.1.189>](Screenshot 2026-02-15 004504.png)
  
  📸 Screenshot: ![Ping Success <172.31.35.134>](Screenshot 2026-02-15 003857.png)

2. SSH into EC2 of VPC 2 and ping private IP of EC2 in VPC 1 and EC2 in default-VPC.

 📸 Screenshot: ![Ping Success <10.0.1.70>](Screenshot 2026-02-15 005232.png)

 📸 Screenshot: ![Ping Success <172.31.35.134>](Screenshot 2026-02-15 005032.png)

3.SSH into EC2 of default-VPC and ping private IP of EC2 in VPC 2 and EC2 in VPC 1.

📸 Screenshot: ![Ping Success <192.168.1.189>](Screenshot 2026-02-15 005609.png)

📸 Screenshot: ![Ping Success <10.0.1.70>](Screenshot 2026-02-15 005409.png)

---

🌐 Traffic Flow 

🔵 Private Communication (VPC1 ➜ VPC2 ➜ VPC3)

Example: EC2 in VPC1 (10.0.1.10) pings VPC2 (192.168.1.10)

Flow:

EC2 (10.0.1.10)
        ↓
Route Table
        ↓
Destination: 192.168.0.0/16
Target: Transit Gateway
        ↓
Transit Gateway
        ↓
VPC2 Route Table
        ↓
EC2 (192.168.1.10)

Reply comes back same path.

🔥 No Internet used
🔥 Centralized routing via TGW

---

🧪 Testing & Verification

From EC2-1:
ping 192.168.1.10
ping 172.16.1.10

Expected Output:

---

🧠 Key Learnings

✅ Transit Gateway acts as central router

Hub-and-spoke model instead of complex peering mesh.

✅ Scalable architecture

One TGW can connect multiple VPCs.

✅ Simplified routing

Instead of multiple peering connections.

✅ Centralized network management

Better for enterprise environment.

✅ Difference from VPC Peering

1. Peering = 1-to-1

2. TGW = Many-to-many

