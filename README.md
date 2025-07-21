# 🌐 Static Web App on AWS S3 + CloudFront (CI/CD via GitHub Actions)

This project demonstrates how to deploy a static website to **Amazon S3**, serve it via **CloudFront**, and automate the deployment using **GitHub Actions**.

---

## 📦 Features

- 🚀 Static site hosted on S3
- 🌍 Global CDN via CloudFront
- 🔄 Automatic deployment on `main` push using GitHub Actions
- 🔐 Secure upload using IAM roles

---

## 🛠️ Prerequisites

- AWS account
- S3 bucket with static website hosting enabled
- CloudFront distribution configured with the S3 bucket as origin
- IAM user with programmatic access and appropriate permissions
- GitHub repository with secrets set

---

## 🔐 GitHub Secrets Required

| Key             | Description                           |
|------------------|---------------------------------------|
| `AWS_ACCESS_KEY_ID`     | Your AWS access key ID          |
| `AWS_SECRET_ACCESS_KEY` | Your AWS secret access key      |
| `AWS_REGION`            | Your AWS region (e.g., `us-east-1`) |
| `S3_BUCKET_NAME`        | Your target S3 bucket name      |

---

## 📁 Project Structure

```
Static-Web-App-on-AWS-S3/
├── .github
│   └── workflows
│       └── deploy.yml      # GitHub Actions workflow
├── index.html              # Your static site files
├── style.css
└── README.md
```

---

## ⚙️ GitHub Actions Workflow

**File: `.github/workflows/deploy.yml`**

```yaml
name:  S3 Syncing workflow

on:
  push:
    branches:
      - main 

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name:  Checkout repository
        uses: actions/checkout@v1

      - name:  Configure AWS credentials
        uses: aws-actions/configure-aws-credentials@v1
        with:
          aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
          aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          aws-region: us-east-1  

      - name:  deploy content to S3 bucket
        run: aws s3 sync . s3://static-web-github-actions --delete


✅ Deployment
Push your static site code to main branch.

GitHub Actions will trigger and deploy to your S3 bucket.

Visit your CloudFront distribution URL to see changes.

📚 References
AWS S3 Docs

AWS CloudFront Docs

AWS CLI

🧑‍💻 Author
Mairaz Khan
DevOps & Cloud Enthusiast
GitHub • LinkedIn


---

### ✅ Download the README.md

Your download is ready:

👉 [Click here to download `README.md`](sandbox:/mnt/data/Static_Web_App_on_AWS_S3_CloudFront_README.md)

Let me know if you'd like to customize anything!
















