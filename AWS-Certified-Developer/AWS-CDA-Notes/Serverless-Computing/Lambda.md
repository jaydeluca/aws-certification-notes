# Lambda
## What is Lambda?
**AWS Lambda** is a compute service where you can upload your code and create a Lambda function. AWS Lambda takes care of provisioning and managing the servers that you use to run the code. You don't have to worry about operating systems, patching, scaling, et.c You can use Lambda in the following ways.
- As an event-driven compute service where AWS Lambda runs your code in response to events. These events could be changes to data in an Amazon S3 bucket or an Amazon DynamoDB table.
- As a compute service to run your code in response to HTTP requests using Amazon API Gateway or API calls made using AWS SDKs.


Lambda is the ultimate abstraction layer. 
You don't have to worry about
   - Data Centers
   - Hardware
   - Assembly Code/Protocols
   - Operating System
   
# Languages
- NodeJS
- Java
- Python
- C#
- Go

# How is Lambda Priced?
- Number of requests
    - First 1 million requests are free. $0.20 per 1 million requests thereafter

- Duration
    - Duration is calculated from the time your code begins executing until it returns or otherwise terminates, rounded up to the nearest 100ms. The price depends on the amount of memory you allocate to your function. You are charged $0.00001667 for every GB-second used.

# Why is Lambda Cool?
- No Servers!
- Continuous Scaling
- Super super cheap!

# Amzaon Echo
- Every time you talk to Amazon Alexa you're talking to a Lambda/the cloud

# Lambda - Exam Tips
- Lambda scales out (not up) automatically
- Lambda functions are independent, 1 event = 1 function
- Lambda is serverless 
- Lambda is a compute service
- Know what services are serverless (Lambda, API Gateway, S3, DynamoDB)
- Lambda functions can trigger other lambda functions, 1 event can = x functions if functions trigger other functions

- Architectures can get extremely complicated, AWS X-ray allows you to debug what is happening
    - If you're asked to debug lambda, which service you should use? AWS X-ray
- Lambda can do things globally, you can use it to back up S3 buckets to other S3 buckets etc
- Know your triggers (popular exam question)

