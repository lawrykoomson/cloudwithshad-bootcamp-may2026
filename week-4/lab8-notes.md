# cloudwithlarry — Lab 8: AI Customer Feedback Hub (Capstone)

## What I Built
- S3 static website with feedback form
- API Gateway (HTTP API) with POST + OPTIONS routes
- Lambda function processing feedback in real time
- Python NLP sentiment analysis (POSITIVE/NEGATIVE/NEUTRAL)
- DynamoDB storing all feedback with sentiment scores
- Full CORS configuration for browser security

## AWS Resources Created
- S3 Bucket: cloudwithlarry-capstone-form (static website)
- DynamoDB Table: cloudwithlarry-feedback
- IAM Role: cloudwithlarry-feedback-role
- Lambda Function: cloudwithlarry-feedback-processor
- API Gateway: cloudwithlarry-feedback-api
  - POST /feedback → Lambda
  - OPTIONS /feedback → Lambda (CORS preflight)
  - Invoke URL: https://k4tr3boi6l.execute-api.us-east-1.amazonaws.com/prod

## Pipeline Flow
Form (S3) → API Gateway → Lambda →
Sentiment Analysis → DynamoDB → Response

## Live Form URL
http://cloudwithlarry-capstone-form.s3-website-us-east-1.amazonaws.com

## Test Result
- Name: Lawrence Koomson
- Message: This AWS bootcamp has been excellent!
- Sentiment: POSITIVE ✅
- Saved to DynamoDB: Yes ✅

## Key Debugging Lessons
- HTTP API CORS needs both API-level config AND Lambda headers
- OPTIONS preflight must return HTTP 200 not 400
- event['httpMethod'] vs event['requestContext']['http']['method']
  differ between REST API and HTTP API Gateway types
- AWS CLI more reliable than console for CORS configuration

## Skills Learned
- API Gateway HTTP API setup
- CORS configuration and debugging
- Lambda + API Gateway integration
- DynamoDB NoSQL storage
- Sentiment analysis with Python NLP
- Full-stack serverless architecture
- Browser preflight requests (OPTIONS)