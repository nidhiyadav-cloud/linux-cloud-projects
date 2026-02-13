# Project 4: EC2 Monitoring with CloudWatch + SNS Alert

## Objective
Automatically monitor EC2 CPU usage and send email alerts if CPU exceeds threshold using AWS CloudWatch and SNS.

## AWS Services Used
- EC2
- CloudWatch (Monitoring & Alarms)
- SNS (Notifications)
- Default VPC

## Architecture Diagram
![Architecture](architecture-diagram.png)

┌─────────────┐
│ EC2 │
│ Instance │
└───────┬─────┘
│ CPU Metrics
▼
┌─────────────┐
│ CloudWatch │
│ Alarm │
└───────┬─────┘
│ Trigger
▼
┌─────────────┐
│ SNS Topic │
│ Email Alert │
└─────────────┘


## Steps to Implement

1. **Create EC2 Instance**  
   - Launch Amazon Linux 2 instance
   - Use default VPC
   - Security Group: Allow SSH (22)

2. **Create SNS Topic**
   - AWS Console → SNS → Topics → Create Topic
   - Name: `EC2-CPU-Alert`
   - Create subscription → Email → verify email

3. **Create CloudWatch Alarm**
   - AWS Console → CloudWatch → Alarms → Create Alarm
   - Select EC2 → CPUUtilization → Your instance
   - Threshold: >= 80% for 1-5 minutes
   - Action → Send notification → SNS Topic `EC2-CPU-Alert`

4. **Test Alarm**
   - SSH into EC2
   - Install stress tool:
     ```bash
     sudo yum install -y stress
     ```
   - Run stress test to increase CPU:
     ```bash
     stress -c 5
     ```
   - You will receive an email alert if alarm triggers

## Interview Explanation
> “Configured CloudWatch to monitor EC2 CPU usage. CloudWatch triggers an SNS email alert if CPU exceeds threshold. Tested using stress command. Demonstrates **proactive monitoring and cloud automation**.”

## Screenshots

1. **CloudWatch Alarm Setup**
![CloudWatch Alarm]()

2. **SNS Topic Confirmation**
![SNS Topic](Screenshot 2026-02-13 220740.png)

3. **Stress Test Running on EC2**
![Stress Test]()

4. **Email Alert Received**
![Email Alert](Screenshot 2026-02-13 221333.png)


