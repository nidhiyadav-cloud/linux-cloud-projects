# Project 1 - AWS EC2 Website Deployment

## 🎯 Objective
Deploy a static website on an AWS EC2 instance using Amazon Linux and Nginx.

## 🧰 Services Used
- Amazon EC2
- Security Group
- Linux (Amazon Linux)
- Nginx Web Server

## 🛠 Steps Performed
1. Launched an EC2 instance using Amazon Linux  
2. Configured Security Group to allow HTTP (80) and SSH (22)  
3. Connected to the instance via SSH  
4. Installed Nginx web server  
5. Started and enabled Nginx service  
6. Deployed a static website  

## 💻 Commands Used
```bash
sudo yum update -y
sudo yum install nginx -y
sudo systemctl start nginx
sudo systemctl enable nginx



