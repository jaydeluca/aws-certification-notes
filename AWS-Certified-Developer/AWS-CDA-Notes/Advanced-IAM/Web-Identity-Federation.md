# Web Identity Federation
**Web Identity Federation** lets you give your users access to AWS resources after they have successfully authenticated with a web-based identity provider like Amazon, Facebook, or Google.

Following successfully authentication, the user receives an authentication code from the Web ID provider, which they can trade for temporary AWS security credentials

## Amazon Cognito
**Amazon Cognito** provides Web Identity Federationg with the following features:
- Sign-up and sign-in to your apps
- Access for guest users
- Acts as an Identity Broker between your application and Web ID provider, so you don't need to write any additional code
- Synchronizes user data for multiple devices 
- Recommended for all mobile applications AWS services

## Amazon Cognito Use Cases
The recommended approach for Web Identity Federation using social media accounts like Facebook

![Image](https://i.imgur.com/w7HRTvB.png)

Cognito brokers between the application and Facebook or Google to provide temporary credentials which map to an IAM role allowing access to the required resources

No need for the application to embed or store AWS credentials locally on the device and it gives the users a seamless experience across all mobile devices.


## Web Identity Federation - Exam Tips
- Federation allows users to authenticate with a Web Identity Provider (Google, Facebook, Amazon)
- The user authenticates first with the Web ID Provider and receives an authentication token, which is exchanged for temporary AWS credentials allowing them to assume an IAM role.
- Cognito is an Identity Broker which handles the interaction between your applications and the Web ID Provider (you don't need to write your own code to do this)
    - Provides sign-up, sign-in, and guest user access
    - Syncs user data for a seamless experience across your devices
    - Cognito is the AWS recommended approach for Web ID Federation particularly for mobile apps
    



