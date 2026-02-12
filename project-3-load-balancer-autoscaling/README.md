# Project 3 - Load Balancer + Auto Scaling

## Objective
Implement high availability architecture using AWS.

## Services Used
- EC2
- AMI
- Launch Template
- Application Load Balancer
- Auto Scaling Group

## Architecture
User → Load Balancer → Target Group → EC2 Instances

## Scaling Config
Min:1
Desired:2
Max:3

## 📸 Screenshots

### Auto Scaling Group Configuration
![ASG Config](Screenshot 2026-02-13 014438.png)

### EC2 Instances Running
![EC2 Instances](Screenshot 2026-02-13 011237.png)

### Target Group Healthy
![Target Group](screenshots/target-group-healthy.png)

### Load Balancer DNS Working
![Load Balancer](screenshots/load-balancer-dns-working.png)

