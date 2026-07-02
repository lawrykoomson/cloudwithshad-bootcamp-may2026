# cloudwithlarry — Lab 6: CI/CD Pipeline

## What I Built
- GitHub repository with HTML website
- S3 bucket with static website hosting
- AWS CodePipeline connecting GitHub to S3
- Auto-deploy triggered by every GitHub push
- Proved with Version 1.0 → Version 2.0 update

## AWS Resources Created
- S3 Bucket: cloudwithlarry-cicd-site
- CodePipeline: cloudwithlarry-cicd-pipeline
- GitHub Connection: cloudwithlarry-github (OAuth)

## Pipeline Stages
Source (GitHub) → Deploy (S3)

## Live Website URL
http://cloudwithlarry-cicd-site.s3-website-us-east-1.amazonaws.com

## GitHub Repo
https://github.com/lawrykoomson/cloudwithlarry-cicd-site

## How It Works
1. Developer pushes code to GitHub main branch
2. CodePipeline detects the change automatically
3. Pipeline pulls the latest code from GitHub
4. Deploys directly to S3 static website hosting
5. Website updates live — zero manual intervention!

## Skills Learned
- AWS CodePipeline setup and configuration
- GitHub OAuth connection to AWS
- S3 static website hosting
- CI/CD concepts — Continuous Integration
  and Continuous Deployment
- Auto-deploy triggered by git push
- Pipeline stages — Source + Deploy