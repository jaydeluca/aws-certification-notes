# API Gateway
# What is an API?
An **API** is an Application Programming Interface

## Types of APIs
- REST APIs (REpresentational State Transfer)
    - Use JSON
    
        ```js
        {   
          "_id": "52326298c929ve92342",
          "firstname": "Ian"
          "team": "Tier3"
        }
        ```
- SOAP APIs (Simple Object Access Protocol)
    - Uses XML
      ```html
      <?xml version = "1.0"?>
          <SOAP-ENV:Envelope
             xmlns:SOAP-ENV = "http://www.w3.org/2001/12/soap-envelope"
             SOAP-ENV:encodingStyle = "http://www.w3.org/2001/12/soap-encoding">
          
             <SOAP-ENV:Body xmlns:m = "http://www.xyz.org/quotation">
                <m:GetQuotationResponse>
                   <m:Quotation>Here is the quotation</m:Quotation>
                </m:GetQuotationResponse>
             </SOAP-ENV:Body>
         </SOAP-ENV:Envelope>
      </xml>
      ```
      
      
 
# What is API Gateway?
**Amazon API Gateway** is a fully managed service that makes it easy for developers to publish, maintain, monitor, and secure APIs at any scale. With a fwe clicks in the AWS Management Console, you can create an API that acts as a "front door" for applications to access data, business logic, or functionality from your back-end services, such as applications running on Amazon Elastic Compute Cloud (Amazon EC2), code running on AWS Lambda, or any web application.

![Image](https://i.imgur.com/5wLDBcJ.jpg)


# What can API Gateway do?
- Expose HTTPS endpoints to define a RESTful API
- Severless-ly connect to services like Lambda & DynamoDB
- Send each API endpoint to a different target
- Run efficiently with low cost
- Scales effortlessly
- Track and control usage by API Key
- Throttle requests to prevent attacks
- Connect to CloudWatch to log all requests for monitoring
- Maintain multiple versions of your API

# How do I configure API Gateway?
- Define an API (container)
- Define Resources and nested Resources (URL Paths)
- For each Resource:
    - Select supported HTTP methods (verbs - GET, PUT, POST, DELETE)
    - Set Security
    - Choose target (such as EC2, Lambda, DynamoDB, etc.
    - Set request and response transformations
- Deploy API to a Stage (QA, STAGE, DEV, PROD)
    - Uses API Gateway domain, by default
    - Can use custom domain
    - Now supports AWS Certificate Manager: free SSL/TLS certs!
    
# What is API Caching?
You can enable **API caching** in Amazon API Gateway to cache your endpoints response. With caching, you can reduce the number of calls made to your endpoint and also improve the latency of the requests to your API When you enable caching for a stage, API Gateway caches responses from your endpoint for a specified time-to-live (TTL) period, in seconds. API Gateway then responds to the request by looking up the endpoint response from the cache instead of making a request to your endpoint.

![Image](https://i.imgur.com/btmMHF1.jpg)

Once the request is cached in API Gateway the response can be returned to the user quickly, without having to go to Lambda.

![Image](https://i.imgur.com/Qn6MYTO.jpg)

# Same Origin Policy
In computing, the **same-origin policy** is an important concept in the web application security model. Under the policy, a web browser permits scripts contained in a first web page to access data in a second web page, but only if both web pages have the same origin.

This is done to prevent Cross-Site Scripting (XSS) attacks.

- Enforced by web browsers
- Ignored by tools like PostMan/Insomnia and Curl.


# Cross-Origin Resource Sharing (CORS)
**Cross-Origin Resource Sharing (CORS)** is one way the server at the other end (not the client code in the browser) can relax the same-origin policy.

Cross-origin resource sharing (CORS) is a mechanism that allows restricted resources (e.g. fonts) on a web page to be requested from another domain outside the domain from which the first resource was served.

- Browsers makes an HTTP OPTIONS call for a URL
    - OPTIONS is an HTTP method like GET, PUT, and POST
- Server returns a response that says:
    "These other domains are approved to GET this URL"
- Error - "Origin policy cannot be read at the remote resource?"
    - You need to enable CORS on API Gateway
    
# API Gateway Exam Tips
- Remember what API Gateway is at a high level
    - API Gateway is the waiter who will take your order to the kitchen and back
- API Gateway has caching capabilities to increase performance
- API Gateway is low cost and scales automatically
- You can throttle API Gateway to prevent attacks
- You can log results to CloudWatch
- If you are using Javascript/AJAX that uses multiple domains with API Gateway, ensure you have enabled CORS on API Gateway
- CORS is enforced by the client

