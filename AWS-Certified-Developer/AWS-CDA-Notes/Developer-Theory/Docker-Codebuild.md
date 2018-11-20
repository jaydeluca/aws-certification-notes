# Docker and CodeBuild
- **Docker** is an Open Source technology which allows you to create applications based on either Linux or Windows containers
- A container is lightweight standalone executable software package which includes everything the software needs to run code, runtime environment, libraries, environment settings etc.
- AWS provides **Elastic Container Service** as a fully managed clustered platform which allows you to run your Docker images in the cloud

- AWS CodeBuild is a fully managed build service which runs a set of commands that you define, e.g. compiles code, runs tests, and produces artifacts that are ready to deploy





1) Retrieve the login command to use to authenticate your Docker client to your registry.
For macOS or Linux systems, use the AWS CLI:
`aws ecr get-login --no-include-email --region us-east-1`

2) If you are using the AWS CLI, run the login command from the output of step 1.
3) Build your Docker image using the following command. For information on building a Docker file from scratch see the instructions here. You can skip this step if your image is already built:

`docker build -t mydockerrepo .`

4) After the build completes, tag your image so you can push the image to this repository:

`docker tag mydockerrepo:latest 582326960667.dkr.ecr.us-east-1.amazonaws.com/mydockerrepo:latest`

5) Run the following command to push this image to your newly created AWS repository:
`docker push 582326960667.dkr.ecr.us-east-1.amazonaws.com/mydockerrepo:latest`






## Docker and CodeBuild - Exam Tips
- Docker Commands to build, tag (apply and alias) and push your Docker image to the ECR Repositry
```
docker build -t myimagerepo .

docker tag myimagerepo:latest 435345345.dkr.ecr.us-east01.amazonaws.com/myimagerepo:latest

docker push 3453523626.dkr.ecr.us-east-1.amazonaws.com/myimagerepo:latest
```

- Use buildsepc.yml to define the build comands and settings used by CodeBuild to run your build
- You can override the settings in buildspec.yml by adding your own commands in the console when you launch the build
- If your build fails, check the build logs in the CodeBuild console and you can also view the full CodeBuild log in CloudWatch