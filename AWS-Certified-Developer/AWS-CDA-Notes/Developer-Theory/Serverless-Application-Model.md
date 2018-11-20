# Serverless Application Model [SAM]
## Introduction to SAM
- **Serverless Application Model (SAM)** is an extension to CloudFormation used to define serverless applications
- Simplified syntax for defining serverless resources: APIs, Lambda functions, DynamoDB tables etc.
- Use the SAML CLI to package your deployment code, upload it to S3 and deploy your serverless application

## SAM CLI Commands
``` 
sam package\
--template-file./mytemplate.yml \
-- output-template-file sam-template.yml\
--s3-bucket s3-bucket-name

sam deploy\
--template-file./mytemplate.yml \
--stack-name mystack\
--capabilities CAPABILITY_IAM
```

## SAM - Exam Tips
- SAM is Serverless Application Model
    - an extension to CloudFormation
- Allows you to define and provision serverless applications using CloudFormation
- Uses the SAM CLI commands to package and deploy:
    - `sam package` - packages your application and uploads to S3
    - `sam deploy` - deploys your serverless app using CloudFormation
    
