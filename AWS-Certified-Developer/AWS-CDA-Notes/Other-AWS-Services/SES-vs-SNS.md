# SES vs SNS
## Amazon SES
**Amazon SES (Simple Email Service)** is a scalable and highly available email service designed to help marketing teams and application developers send marketing, notification, and transactional emails to their customers using a pay as you go model.

Can also be used to receive emails: incoming emails can be delivered automatically to an S3 bucket

Incoming mails can be used to trigger Lambda functions and SNS notifications

## Amazon SES Use Cases
- Automated Emails
- Purchase Confirmations, shipping notifications, order status updates
    - e.g. a mobile phone company that needs to send automated confirmation email every time a customer purchases pre-paid mobile phone minutes 
- Marketing communications, advertisements, newsletters, special offers
    - e.g. an online retail business that needs to let customers know about sales promotions and discounts


![Image](https://i.imgur.com/2Lt7uaZ.jpg)


## SES vs SNS - Exam Tips
- Remember that SES is for email only
- It can be used for incoming and outgoing mail
- It is not subscription based, you only need to know the email address

- SNS supports multiple formats (SMS, SQS, HTTP, Email)
- Push notifications only
- Pub-Sub model: consumers must subscribe to a topic
- You can fan-out messages to large number of recipients
    - e.g. multiple clients each with their own SQS queue


