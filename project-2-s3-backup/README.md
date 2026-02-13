# Project 2 – Automated Backup to S3

## 🎯 Objective
Automate Linux folder backup to AWS S3 using Shell Script and Cron.

## 🧰 Services Used
- AWS EC2
- AWS S3
- AWS IAM
- AWS CLI
- Cron
- Shell Scripting

## ⚙️ Steps Performed
1. Created S3 bucket
2. Created an IAM user
3. Created an Access Keys
4. Installed AWS CLI
5. Created backup script
6. Uploaded backup to S3
7. Automated using Cron

## 🏗 Architecture

┌─────────────────────────────┐
│       Linux EC2             │
│ src: /home/ec2-user/backup/data │
│ backup.sh script            │
└─────────────┬───────────────┘
              │ Cron Job (Daily)
              ▼
┌─────────────────────────────┐
│ Compressed Backup File      │
│ dest: /tmp/data-YYYYMMDD-HHMMSS.tar.gz │
└─────────────────────────────┘


## 💻 Script Used
```bash
#!/bin/bash

SRC="/home/ec2-user/backup/data"
DEST="/tmp/data-$(date +%Y%m%d-%H%M%S).tar.gz"
BUCKET="s3://nidhi-backup-2026"

tar -czf $DEST $SRC
aws s3 cp $DEST $BUCKET

## 📸 Screenshots

![Script](Screenshot 2026-02-13 001234.png)
![S3 Upload](Screenshot 2026-02-13 001512.png) and (Screenshot 2026-02-13 000642.png)
![Cron Job](RHEL2-2026-02-12-23-54-31.png)

