# Project 5: Static Website Hosting using S3 + CloudFront

## 🎯 Objective
To host a static website using Amazon S3 and distribute it globally using CloudFront CDN.

---

## 🛠️ AWS Services Used
- S3
- CloudFront
- IAM
- Default VPC

---

## 🏗️ Architecture Diagram

User
   ↓
CloudFront
   ↓
S3 Bucket
   ↓
Static Website Files (index.html)


---

## 🔹 Implementation Steps

### Step 1: Created S3 Bucket
- Disabled block public access
- Uploaded index.html

📸 Screenshot:
![S3 Bucket](screenshots/1-s3-bucket.png)

---

### Step 2: Enabled Static Website Hosting
- Enabled static hosting
- Index document: index.html

📸 Screenshot:
![Static Hosting](screenshots/2-static-hosting.png)

---

### Step 3: Added Bucket Policy
- Allowed public read access

📸 Screenshot:
![Bucket Policy](Screenshot 2026-02-13 225802.png
)

---

### Step 4: Created CloudFront Distribution
- Selected S3 as origin
- Used default cache behavior

📸 Screenshot:
![CloudFront](screenshots/4-cloudfront.png)

---

### Step 5: Website Accessed via CloudFront
- Accessed website using CloudFront URL

📸 Screenshot:
![Final Website

---

## 💬 Interview Explanation

"I hosted a static website using Amazon S3 and configured public access via bucket policy. Then I created a CloudFront distribution to deliver the website globally with low latency. This demonstrates my understanding of S3, CDN, and secure public hosting in AWS."

---

## ✅ Key Learning
- Static website hosting
- Bucket policy configuration
- CDN distribution using CloudFront
- Public access management

