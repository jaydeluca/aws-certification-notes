1) Create a custom VPC

2) Create a Subnet

3) Create a Internet Gateway (IGW)

4) Attach IGW to custom VPC

5) Create a route table and associate the subnet and IGW

6) Create a service IAM role for EC2 to access s3

7) Spin up an EC2 Instance

      a. Associate with custom VPC

      b. Enable auto assign public IP

      c. Attach created s3 access role in step 6

      d. Add a name tag for code-deploy service to use later
8) Install code-deploy SDK in EC2 instance

      a. sudo yum update

      b. sudo yum install ruby

      c. sudo yum install wget

      d. cd /home/ec2-user

      e. wget https://aws-codedeploy-eu-central-1.s3.amazonaws.com/latest/install

      f. chmod +x ./install

      g. sudo ./install auto

      h. sudo service codedeploy-agent status
9) Create a s3 bucket with public read access

10) Create a IAM user with code-deploy access

11) In local environment, perform aws configure with user created in step 10

12) Create your application.zip and load it into CodeDeploy from local environment

     a. aws deploy create-application --application-name mywebapp

     b. aws deploy push --application-name mywebapp --s3-location s3://<MY_BUCKET_NAME>/webapp.zip --ignore-hidden-files

13) Create a service role in IAM for code-deploy to access EC2

14) Create a deployment group in code-deploy for the application created from local

    a. Choose in-place deployment since this is a brand-new application

    b. Associate the EC2 from step 7 using the tag

    c. Choose CodeDeployDefault.AllAtOnce

    d. Associate the service role created in step 13
15) Deploy new revision from the created deployment group

    a. S3 repository type

    b. Revision location auto populates from s3 bucket

    c. Leave everything else default
16) Finally, to verify deployment, load public IP from EC2 instance in the browser