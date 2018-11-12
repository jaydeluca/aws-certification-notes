# RDS & Elastic Beanstalk
Elastic Beanstalk supports two ways of integrating an RDS database with your Beanstalk environment.

You can launch the RDS instance from within the Elastic Beanstalk console, which means the RDS instance is created within your Elastic Beanstalk environment - a good option for DEV and Test deployments.

However, this may not be ideal for production environments because it means the lifecycle of yor database is tied to the lifecycle of your application environment. If you terminate the environment, the database instance will be terminated too.

For Production environments, the preferred option is to decouple the RDS instance from your EBS environment: i.e. launch it outside of Elastic Beanstalk, directly from RDS section of the console.

This option gives you a lot more flexibility, allows you to connect multiple environments to the same database, provides a wider choice of database types, and allows you to tear down your application environment without affecting the database instance.

## Access to RDS from Elastic Beanstalk
To allow the EC2 instances in your Elastic Beanstalk environment to connect to an outside database, there are two additional configuration steps required:
   - An additional Security Group must be added to your environment's Auto Scaling group
   - You'll need to provide connection string configuration information to your application servers (endpoint, password using Elastic Beanstalk environment properties)
   
   
## RDS & Elastic Beanstalk - Exam Tips
- Two different options for launching your RDS instance:
- **Launch wihtin Elastic Beanstalk**
   - When you terminate the Elastic Beanstalk environment, the database will also be terminated
   - Quick and easy to add your database and get started
   - Suitable for Dev and Test environments only
- **Launch outside of Elastic Beanstalk**   
   - Additional Configuration steps required- Security Group and Connection information
   - Suitable for Production envrionments, more flexibility
   - Allows connection from multiple environments, you can tear down the application stack without impacting the database
   
   
   
   