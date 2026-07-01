# cloudwithlarry — Lab 4: Serverless Image Resizer

## What I Built
- S3 bucket with uploads/ and thumbs/ folders
- IAM role with Lambda + S3 permissions
- Lambda function (Python 3.12) using Pillow
- Pillow Lambda Layer (Klayers-p312-Pillow:11)
- S3 trigger on uploads/ prefix
- Auto-resizes any uploaded image to 300x300px

## AWS Resources Created
- S3 Bucket: cloudwithlarry-resizer-lk-2026
- IAM Role: cloudwithlarry-resizer-role
- Lambda Function: cloudwithlarry-resize-image
- Runtime: Python 3.12
- Memory: 512MB | Timeout: 30s
- Layer: arn:aws:lambda:us-east-1:770693421928:layer:Klayers-p312-Pillow:11

## How It Works
1. User uploads image to S3 uploads/ folder
2. S3 fires an event to Lambda automatically
3. Lambda downloads the image from S3
4. Pillow resizes it to max 300x300px
5. Lambda saves thumbnail to S3 thumbs/ folder
6. Zero servers, zero SSH, zero management!

## Key Concepts Learned
- Serverless event-driven architecture
- Lambda triggers from S3 events
- Lambda Layers for external libraries
- Pillow image processing in Python
- IAM roles for Lambda permissions
- Infinite loop prevention with prefix check
- No module named PIL fix via Klayers

## Same Pattern Powers
- Instagram thumbnail generation
- WhatsApp image compression
- E-commerce product image galleries
- Document scanning services