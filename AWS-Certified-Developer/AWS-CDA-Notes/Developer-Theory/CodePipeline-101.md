# CodePipeline
AWS CodePipeline

**AWS CodePipeline** is a fully managed Continuous Integration and Continuous Delivery service.

CodePipeline can orchestrate the Build, Test, and even Deployment of your application every time there is a change to your code - all based on a user defined software release process.

Traditional manual approaches to code delivery can be slow and prone to errors, whereas an automated process allows developers to frequently release new features and bug fixes in a fast and reliable way.

CodePipeline allows you to model your release process as a workflow or pipeline made up of different tasks, such as the simple workflow represented below.

![Image](https://i.imgur.com/9hE96MK.png)

You define what happens and where for each of the different stages of the workflow, and this can be modelled using the CodePipeline GUI or CLI.

Integrates with CodeCommit, CodeBuild, CodeDeploy, Lambda, ElasticBeanstalk, CloudFormation, Elastic Container Service as well as third party tools like Github and Jenkins


Every code change pushed to your code repository automatically enters the workflow and triggers the set of actions defined for each stage of the pipeline.

The pipeline will automatically stops if one of the stages fails. For example, if one of your automated unit tests fails. This means that bugs are caught before the code is deployed while they are still easy to fix.


#### Example
![Image](https://i.imgur.com/rIhF5v5.jpg)

## AWS CodePipeline - Exam Tips
- Continuous Integration / Continuous Delivery service
- Automates your end-to-end software release process based on a user defined workflow
- Can be configured to automatically trigger your pipeline as soon as a change is detected in your source code repository
- Integrates with other services from AWS like CodeBuild and CodeDeploy, as well as third party and custom plugins


