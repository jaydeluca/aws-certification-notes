# Severless Summary
## Lambda - Exam Tips
 - Lambda scales out (not up) automatically
    - You can have many Lambda functions running at once
- Lambda functions are independent, 1 event = 1 function
- Lambda is serverless
- Know what services are serverless
    - DynamoDB, S3, Lambda, EC2, Elastic Beanstalk
- Lambda functions can trigger other functions, 1 event can = x functions if functions trigger other functions

- Architecture can get extremely complicated, AWS X-Ray allows you to debug what is happening 
- Lambda can do things globally, you can use it to back up S3 buckets to other S3 buckets etc.
- **Know your Lambda triggers**
    - API Gateway
    - AWS IoT
    - Cloudwatch Events
    - Cloudwatch Logs
    - Code Commit
    - Cognito Sync Trigger
    - DynamoDB
    - Kinesis
    - S3
    - SNS
    - SQS
    
## API Gateway - Exam Tips
- Remember what API Gateway is a high level
- API Gateway has caching capabilities to increase performance
- API Gateway is very low cost and scales automatically
- You can throttle API Gateway to prevent attacks
- You can log results to CloudWatch
- If you are using Javascript/AJAX that uses multiple domains with API Gateway, ensure that you have enabled CORS on API Gateway
- CORS is enforced by the client

## Version Control with Lambda - Exam Tips
- Can have multiple versions of lambda functions
- Latest version will use $LATEST
- Qualified version will use $LATEST, unqualified version will not have it
- Version are immutable (Cannot be changed)
- Can split traffic using aliases to different versions
    - Cannot split traffic with $LATEST, instead create an alias to latest

## Step Functions - Exam Tips
- Great way to visualize your serverless application
- Step Functions automatically triggers and tracks each step
- Step Functions logs the state of each step so if something goes wrong you can track what went wrong and where

# X-Ray - Exam Tips
The X-Ray SDK provides:
  - Inteceptors to add to your code to trace incoming HTTP requests
  - Client handlers to instrument AWS SDK clients that your application uses to call other AWS services
  - An HTTP client to use to instrument calls to other internal and external HTTP web services
  
The X-Ray Integrates with  the following AWS services:
- Elastic Load Balancer
- AWS Lambda
- Amazon API Gateway
- Amazon Elastic Compute Cloud
- AWS Elastic Beanstalk

X-Ray Supported Languages:
- Java
- Go
- NodeJS
- Python
- Ruby
- .Net
