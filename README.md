![AWS](https://img.shields.io/badge/AWS-Lambda-orange)
![Python](https://img.shields.io/badge/Python-boto3-blue)
![CloudFormation](https://img.shields.io/badge/IaC-CloudFormation-yellow)
![DynamoDB](https://img.shields.io/badge/DB-DynamoDB-blue)
![License](https://img.shields.io/badge/License-MIT-green)

# ☁️ AWS Cloud Cost Sentinel

> Serverless solution to automatically detect and delete orphaned AWS resources — reducing cloud waste with one-click cleanup.

---

## 🚨 The Problem: Cloud Waste

- Unused resources silently accumulate in AWS accounts
- They keep billing even when not in use
- Examples: Unattached EBS volumes, unused Elastic IPs, empty S3 buckets, orphaned EFS
- Leads to **budget overruns** and messy cloud environments

---

## ✅ The Solution

A fully serverless, automated system that **scans, lists, and deletes** orphaned AWS resources through a clean UI — deployed via CloudFormation in any AWS account.

---

## 🏗️ Architecture

| Component | Role |
|---|---|
| **Scanner Lambda** | Scans AWS account for orphaned resources |
| **Delete Lambda** | Removes selected resources on demand |
| **DynamoDB** | Stores scanned resource list |
| **API Gateway** | Secure REST API for frontend communication |
| **GitHub Pages** | Hosts the interactive frontend UI |
| **CloudFormation** | Full IaC deployment |

---

## 🔄 End-to-End Workflow

```
