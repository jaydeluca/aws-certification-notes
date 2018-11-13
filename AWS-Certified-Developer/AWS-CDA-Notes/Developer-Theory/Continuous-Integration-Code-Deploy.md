# Continuous Integration & Code Deliver/Deploy
[CI/CD White Paper](https://d1.awsstatic.com/whitepapers/DevOps/practicing-continuous-integration-continuous-delivery-on-AWS.pdf)

- CI/CD are Best Practices for software development and deployment
- They enable frequent software changes to be applied whilst maintaining system and service stability
- Companies like AWS, Netflix, Google, and Facebook have pioneered this approach to releasing code, successfully applying thousands of changes per day


## Continuous Integration Workflow
![Image](https://i.imgur.com/GNIdWkY.png)
- Multiple developers working on different features or bug fixes
- All contributing to the same application
- Sharing the same code repository (e.g. git)
- Frequently pushing their updates into the shared repo 

[!Image](https://i.imgur.com/9WZAire.png)
- Code repository integrated with a build management system
- Code changes trigger an automated build
- We need a way to ensure that any code change does not break the build or introduce new bugs in the application

![Image](https://i.imgur.com/7OMaTq5.png)
- The test system runs automated tests on the newly built application
- Identifies any bugs, preventing issues from being introduced in the master branch
- CI Focusses on small code changes which get commited frequently once they've been tested


## Continuous Deliver/Deployment
- CD can mean either Continuous Delivery or Continuous Deployment
- Continuous Delivery is a Development practice where merged changes are automatically built, tested, and prepared for release into staging and eventually production environments.
- There is usually a manual decision process to initiate deployment of the new code

![Image](https://i.imgur.com/leSXtW0.jpg)

- Continuous Deployment takes the idea of automation one step further and automatically deploys the new code following successful testing, eliminating any manual steps
- The new code is automatically released as soon as it passes throug the stages of your release process (build, test, package)
- Small changes are released early and frequently
- Both practices require the build, test, and deployment processes to be fully automated but Continuous Deployment also automates the release process as well

![Image](https://i.imgur.com/wgQKsB8.jpg)

## AWS Continuous Integration & Continuous Deployment Tools

![Image](https://i.imgur.com/F0xe5Yu.jpg)


## CI/CD - Exam Tips
- Definitely worht a few points in the exam
- Worth reading the whitepaper (https://d1.awsstatic.com/whitepapers/DevOps/practicing-continuous-integration-continuous-delivery-on-AWS.pdf)
- Continuous Integration is about integrating or merging the code changes frequently - at least once per day, enables multiple devs to work on the same application
- Continuous Delivery is all about automating the build, test, and deployment functions
- Continuous Deployment fully automates the entire release process, code is deployed into Production as soon as it has successfully passed through the release pipline
- AWS CodeCommit - Source Control service (Git)
- AWS CodeBuild - compile source code, run tests and package code
- AWS CodeDeploy - Automated deployment to EC2, on premise systems and Lambda
- AWS CodePipeline - CI/CD workflow tool, fully automates the entire release process (build, test, deployment)
