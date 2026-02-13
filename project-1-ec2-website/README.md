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

 ## 🏗 Architecture
          ┌─────────────┐
          │   Users     │
          └─────┬───────┘
                │ HTTP/HTTPS
          ┌─────▼───────┐
          │   EC2       │
          │ Instance    │
          │ (Nginx)     │
          └─────┬───────┘
        User Data Script (on boot):
        ┌─────────────────────────────┐
        │ - yum install nginx         │
        │ - start & enable nginx      │
        │ - echo "This is AWS and     │
        │    this is my $(hostname)"  │
        │    > index.html             │
        └─────────────────────────────┘


## 💻 Commands Used
```bash
sudo yum update -y
sudo yum install -y nginx firewalld
sudo systemctl enable nginx
sudo systemctl start nginx
sudo systemctl enable firewalld
sudo systemctl start firewalld
firewall-cmd --permanent --add-service=http
echo "welcome to aws and this is my $(hostname)" >/usr/share/nginx/html/index.html

## 📸 Screenshots

### EC2 Running
![EC2](Screenshot 2026-02-12 203804.png)

### Security Group
![SG](Screenshot 2026-02-12 204902.png)

### Nginx Output
![Nginx](Screenshot 2026-02-12 204053.png)

### Website Output
![Website](Screenshot 2026-02-12 204800.png)



