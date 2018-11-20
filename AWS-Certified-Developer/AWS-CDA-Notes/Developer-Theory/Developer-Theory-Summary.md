# Developer Theory - Summary
## Continuos Integration/Continuous Deployment
- Definitely worth a few points in the exam
- Worth reading the white paper:
    - https://d0.awsstatic.com/whitepapers/DevOps/practicing-continuous-integration-continuous-delivery-on-AWS.pdf
- Continuous Integration is about integration or merging the code changes frequently
    - at least once per day, enables multiple devs to work on the same application
- Continuous Delivery is all about automating the build, test, and deployment functions
- Continuous Deployment fully automates the entire release process, code is deployed into Production as soon as it has successfully passed through the release pipeline

- AWS CodeCommit - Source control service (GIT)
- AWS CodeBuild - compile source code, run tests, and package code
- AWS CodeDeploy - Automated deployment to EC2, on premises systems and Lambda
- AWS CodePipeline - CI/CD workflow tool, fully automates the entire release process (build, test, deployment)

## AWS CodeCommit
- AWS CodeCommit
    - Based on git
    - Centralized repository for all your code, binaries, images, and libraries
    - Tracks and manges code changes
    - Maintains version history
    - Manages updates from multiple sources and enables collaboration

## AWS Code Deploy
- AWS CodeDeploy is a fully managed automated deployment service and can be used as part of a Continuous Delivery or Continuous Deployment process
- Remember the different types of deployment approach:
    - **In-Place or Rolling Update** - you stop the application on each host and deploy the latest code. EC2 and on premise systems only. To roll back you must re-deploy the previous version of the application.
    - **Blue/Green** - New instances are provisioned and the new application is deploy to these new instances. Traffic is routed to the new instances according to your own schedule. Supported for EC2, on-premise systems and Lambda functions. Rollback is easy, just route the traffic back to the original instances. Blue is the active deployment, green is the new release.

- The AppSpec file defines all the parameters needed for the deployment e.g. location of application files and pre/post deployment validation tests to run
- For EC2/ On Premises systems, the appspec.yml file must be placed in the rot directory of your revision (the same folder the contains your application code)
- Lambda supports YAML or JSON

- The **Run Order of Hooks** in a CodeDeploy deployment
    - BeforeBlockTraffic -> BlockTraffic -> AfterBlockTraffic
    - ApplicationStop
    - BeforeInstall
    - Install
    - AfterInstall
    - ApplicationStart
    - ValidateService
    - BeforeAllowTraffic -> AllowTraffic -> AfterAllowTraffic
    

## AWS CodePipeline
- Continuous Integration / Continuous Delivery Service
- Automates your end-to-end software release process based on a user defined workflow
- Can be configured to automatically trigger your pipeline as soon as a change is detected in your source code repository
- Integrates with other services from AWS like CodeBuild and CodeDeploy, as well as third party and custom plugins


## Docker
- Docker allows you to package up your software into Containers which you can run in Elastic Container Service (ECS)
- A Docker container includes everything the software needs to run including code, libraries, runtime and environment variables etc.
- We use a special file called a Dockerfile to specify the instructions needed to assemble your Docker image
- Once built, Docker images can be stored in Elastic Container Registry (ECR) and ECS can then use the image to launch Docker containers
- Docker Commands to build, tag (apply and alias) and push your Docker image to the ECR Repositry
```
docker build -t myimagerepo .

docker tag myimagerepo:latest 435345345.dkr.ecr.us-east01.amazonaws.com/myimagerepo:latest

docker push 3453523626.dkr.ecr.us-east-1.amazonaws.com/myimagerepo:latest
```


## AWS CodeBuild
- CodeBuild is a fully managed build service. It can build source code, run tests and produce software packages based on commands that you define yourself
- By default the buildspec.yml defines the build commands and settings used by CodeBuild to run your build
- You can completely override the settings in buildspec.yml by adding your own commands in the console when you launch the build
- If your build fails, check the build logs in the CodeBuild console and you can also view the full CodeBuild log in CloudWatch 


