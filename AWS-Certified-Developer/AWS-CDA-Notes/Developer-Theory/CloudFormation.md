# CloudFormation
## Introductoin to CloudFormation
- CloudFormation is a service that allows you to manage, configure and provision your AWS infrastructure as code
- Resources are defined as using a CloufFormation Template
- CloudFormation interprets the template and makes the approporate API calls to create the resources you have defined
- Supports YAML or JSON

## CloudFormation Benefits
- Infrastructure is provisioned consistently, with fewer mistakes
- Less time and effort than configuring things manually
- You can use version control and peer review your templates
- Free to use (charged for what you create)
- Can be used to manage updates & dependencies
- Can be used to rollback and delete the entire stack as well


## CloudFormation Template
- YAML or JSON template used to describe the endstate of the infrastructure you are either provisioning or changing
- After creating the template, you upload it to CloudFormation using S3
- CloudFormation reads the template and makes the API calls on your behalf
- The resulting resources are called a Stack


![Image](https://i.imgur.com/KO0Hqp1.jpg)


![Image](https://i.imgur.com/tkPXBCV.jpg)

![Image](https://i.imgur.com/4FGbHnx.jpg)

##### CloudFormation snippets
https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/CHAP_TemplateQuickRef.html


## CloudFormation - Exam Tips
- **CloudFormation** allows you to manage, configure and provision AWS infrastructure as code (YAML/JSON)
- Remember the main sections in the CloudFormation template:
    - Parameters - input custom values
    - Conditions - e.g. provision resources based on environment
    - Resources - mandatory - the AWS resources to create
    - Mappings - create custom mappings like Region : AMI
    - Transforms - reference code located in S3 e.g. Lambda code or reusable snippets of CloufFormation code

- Resources is the only mandatory section of the CloudFormation template
- Remember that the **Transform** section is used to references addiontal code stored in S3, allowing for code re-use, e.g. for Lambda code or template snippets / reusable pieces of CloudFormation code



