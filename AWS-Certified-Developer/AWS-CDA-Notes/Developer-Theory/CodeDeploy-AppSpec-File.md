# Advanced CodeDeploy the AppSpec File
## AppSpec File - Lambda Deployments
**The AppSpec File** is used to define the parameters that will be used for a CodeDeploy deployment. The file structure depends on whether you are deploying to Lambda or EC2 / On Premises.

For Lambda deployments, the AppSpec File may be written in YAML or JSON and contains the following fields:
- **version:** Reserved for future use - currently the only allowed value is 0.0
- **resources:** The name and properties of the Lambda function to deploy
- **hooks:** Specifies Lambda functions to run a set points in the deployment lifecycle to validate the deployment e.g. validation tests to run before allowing traffic to be sent to your newly deployed instances

## appsepc.yml file - Lambda Example
```yml 
version: 0.0
resources:
-myLambdaFunction:
    Type: AWS::Lambda::Function
    Properties:
        Name:"myLambdaFunction"
        Alias:"myLambdaFunctionAlias"
        CurrentVersion:"1"
        TargetVersion:"2"
hooks:
    -BeforeAllowTraffic:"LambdaFunctionToValidateBeforeTrafficShift"
    AfterAllowTraffic:"LambdaFunctionToValidateAfterTrafficShift"
```

## AppSpec File - Hooks - Lambda
The following hooks are available for use:
- **BeforeAllowTraffic** - used to specify the tasks or functions you want to run before traffic is routed to the newly deployed Lambda function (e.g. test to validate that the function has been deployed correctly)
- **AfterAllowTraffic** - used to specify the tasks or functions you want to run after the traffic has been routed to the newly deployed Lambda function. (e.g. test to validate that the function is accepting traffic correctly and behaving as expected)

## AppSpec File - Hooks - EC2 and On Premises
- **version:** reserved for future use- currently the only allowed value is 0.0
- **os:** the Operating System version you are using e.g. linux , windows
- **files:** The location of any application files that need to be copied and where they should be copied to (source and destination folders)
- **hooks:** Lifecycle event hooks allow you to specify scripts that need to run at set points in the deployment lifecycle (e.g. to unzip application files prior to deployment, run functional tests on the newly deploy application, and to de-register and re-register instances with a load balancer)


For EC2 and On Premises deployments, the appspec.yml must be placed in the **root of the directory of your revision** - this is the directory containing your application source code, otherwise the deployment will fail

Typical setup looks like this:
```
mywebapp
    \- appspec.yml
    |- /Scripts
    |- /Config
    |- /Source 
```

## appspec.yml File - EC2 Example
```
version: 0.0
os: linux
files:
    -source: Config/config.txt
     destination: /webapps/Config
    - source: Source
     destination: /webapps/myApp
```

``` 
hooks:
    BeforeInstall:
        -location: Scripts/UnzipResourceBundle.sh
        -location: Scripts/UnzipDataBundle.sh
    AfterInstall:
        -location: Scripts/RunResourceTests.sh
         timeout:180
```

```
ApplicationStart:
    - location: Scripts/RunFunctionalTests.sh
     timeout: 3600
     
ValidateService:
    - location: Scripts/MonitorService.sh
     timeout: 3600
     runas: codedeployuser

```


## AppSpec File - Supported Hooks for EC2 and On Premises
- BeforeBlockTraffic - run tasks on instances before they are deregistered from a load balancer
- BlockTraffic - Deregister instances from a load balancer
- AfterBlockTraffic - Run tasks on instances after they are deregistered from a load balancer

## AppSpec File - Hooks for EC2  and On Premises
- ApplicationStop - Gracefully stop the application in preparation for deploying the new revision
- DownloadBundle - the CodeDeploy agent copies the application revision files to a temporary location
- BeforeInstall - Details of any pre-installation scripts, e.g. backing up the current version, decrypting files
- Install - The CodeDeploy agent copies the application revision files from their temporary location to their correct location
- AfterInstall - Details of any post-installation scripts e.g. configuration tasks to change file permission
- ApplicationStart - Restarts any services that were stopped during ApplicationStop
- ValidateService - Details of any tests to validate the service
- BeforeAllowTraffic - Run tasks on instances before they are registered with a load balancer
- AllowTraffic - Register instances with a load balancer
- AfterAllowTraffic - Run tasks on instances after they are registered with a load balancer

![Image](https://i.imgur.com/0ljgqpr.jpg)

## Run Order of Hooks
3 Stages of a CodeDeploy deployment
- Set of tasks need to run to de-register from load balancer
- Set of tasks needed to run in order to upgrade application
- Set of tasks needed to run to re-register load balancer

## CodeDeploy Advanced Settings - Exam Tips
- The appspec.yml file defines all parameters needed for deployment e.g. location of application files and pre/post deployment validations tests to run
- For EC2/On Premises systems, the appspec.yml file must be placed in the root direcrory of your revision (the same folder that contains your application code). Written in YAML
- Lambda supports YAML or JSON

- The run order of hooks in a CodeDeploy deplpyment:
    - BeforeBlockTraffic -> BlockTraffic -> AfterBlockTraffic
    - ApplicationStop
    - BeforeInstall
    - Install
    - AfterInstall
    - ApplicationStart
    - ValidateService
    - BeforeAllowTraffic -> AllowTraffic -> AfterAllowTraffic
    

