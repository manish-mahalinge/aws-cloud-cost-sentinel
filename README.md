![AWS](https://img.shields.io/badge/AWS-Lambda-orange)
![Python](https://img.shields.io/badge/Python-boto3-blue)
![CloudFormation](https://img.shields.io/badge/IaC-CloudFormation-yellow)
![DynamoDB](https://img.shields.io/badge/DB-DynamoDB-blue)

# AWS Cloud Cost Sentinel

I built this project because I noticed how easy it is to forget about AWS resources after you're done testing — and those forgotten resources keep silently charging you. This tool scans your AWS account, shows you what's orphaned, and lets you delete it all in one click.

---

## Why I Built This

Working with AWS, I kept running into the same problem — old EBS volumes, unused Elastic IPs, forgotten S3 buckets just sitting there costing money. I wanted a simple dashboard where I could see everything in one place and clean it up without jumping between 10 different AWS console pages.

---

## How It Works

Two Lambda functions do the heavy lifting:

- **Scanner** — goes through your AWS account and finds resources that aren't attached to anything
- **Delete** — removes whatever you select from the UI

Results get stored in DynamoDB so the UI can display them. API Gateway connects the frontend to the backend. The whole thing is deployed via CloudFormation so you can spin it up in any AWS account in minutes.

```
Scanner Lambda → DynamoDB → API Gateway → Frontend UI → Delete Lambda
```

---

## What It Catches

- Unattached EBS volumes
- Unused Elastic IPs
- Empty/orphaned S3 buckets
- Unused EFS file systems

---

## Tech Used

`AWS Lambda` `DynamoDB` `API Gateway` `CloudFormation` `SNS` `Python (boto3)` `GitHub Actions` `GitHub Pages`

---

## Deploying It Yourself

```bash
git clone https://github.com/manish-mahalinge/aws-cloud-cost-sentinel
cd aws-cloud-cost-sentinel

aws cloudformation deploy \
  --template-file OrphanedResourceHunter.yaml \
  --stack-name cloud-cost-sentinel \
  --capabilities CAPABILITY_IAM

