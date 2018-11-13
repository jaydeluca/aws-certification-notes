# CodeDeploy 101
- **AWS CodeDeploy** is an automated deployment service which allows you to deploy your application code automatically to EC2 instances, on-premise systems and Lambda functions
- Allows you to quickly release new features, avoid downtime during application deployments, and avoid the risks associated with manual processes
- Automatically scales with your infrastructure and integrates with various CI/CD tools, e.g. Jenkin, Github, Atlassian, AWS CodePipeline as well as config management tools like Ansible, Puppet, Chef

- Two deployment approaches available:
    - In Place and Blue/Green
    
## Deployment Options - In-Place Deployment

![Image](https://i.imgur.com/qP0P8Gn.png)
- The application is stopped on each instance and the latest revision is installed
- The instance is out of service during this time and your capacity will be reduced
- If the instances are behind a load balancer, you can configure the load balancer to stop sending requests to the instances which are being upgraded
- In-Place upgrade is also known as a Rolling Update
- It can only be used for EC2 and on-premise systems - it is not supported for Lambda
- If you need to roll back your changes, the previous version of the application will need to be re-deployed

## Deployment Options - Blue/Green Deployment

![Image](https://i.imgur.com/8qF0jIY.png)
- Blue/Green deployment - New Instances are provisioned and the latest revision is installed on the new instances. Blue represents the active deployment, green is the new release.
- The new instances are registered with an Elastic Load Balancer, traffic is then routed to the new instances and the original instances are eventually terminated
- Advantages of a Blue/Green deployment are that the new instances can be created ahead of time and the code released to production by simply switching all traffic to the new servers
- Switching back to the original environment is faster and more reliable and is just a case of routing the traffic back to the original servers (as long as you haven't already terminated them)

## AWS CodeDeploy - Terminology
- **Deployment Group** - A set of EC2 instances or Lambda functions to which a new revision of the software is to be deployed
- **Deployment** - The process and components used to apply a new revision
- **Deployment Configuration** - A set of deployment rules as well as success/failure conditions used during a deployment
- **AppSec File** - Defines the deployment actions you want AWS CodeDeploy to execute
- **Revision** - Everything needed to deploy the new version: AppSec file, application files, executables, config files
- **Application** - Unique identifier for the application you want to deploy. To ensure the correct combination of revision, deployment configuration and deployment group are referenced during a deployment

## AWS CodeDeploy - Exam Tips
- AWS CodeDeploy is a fully managed automated deployment service and can be used as part of a Continuous Delivery or Continuous Deployment process
- Remember the different types of deployment approach:
    - **In-Place or Rolling Update** - you stop the application on each host and deploy the latest code. EC2 and on-premise systems only. To roll back you must re-deploy the previous version of the application
    - **Blue/Green** - new instances are provisioned and the new application is deployed to these new instances. Traffic is routed to the new instances according to your own schedule. Supported for EC2, on-premise systems, and Lambda functions. Roll back is easy, just route the traffic back to the original instances. Blue is the active deployment, green is the new release.


