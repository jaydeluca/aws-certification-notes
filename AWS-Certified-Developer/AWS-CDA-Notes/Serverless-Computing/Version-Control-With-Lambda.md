# Version Control With Lambda
## Versioning
When you use **versioning** in AWS Lambda, you can public one or more versions of your Lambda function. As a result, you can work with different variations of your Lambda function in your development workflow, such as development, beta, and production.

Each Lambda function version has a unique Amazon Resource Name (ARN). After you public a version, it is immutable (that is, it can't be changed).

AWS Lambda maintains the latest function code in **$LATEST** version. When you update your function vode, AWS Lambda replaces the code in the $LATEST version of the Lambda function.

## Qualified/Unqualified ARNs
- You can refer to this function using its Amazon Resource Name (ARN). There are two ARNs associated with this initial version:
    - Qualified ARN - The function ARN with the version suffix.
        - arn:aws:lambda:aws-region:acct-id:function:helloworld:$LATEST
    - Unqualified ARN - The function ARN without the version suffix.
        - arn:aws:lambda:aws-region:acct-id:function:helloworld
## Alias
After initially created a Lambda function (the $LATEST version), you can publish a version 1 of it. By creating an alias named PROD that points to version 1, you can now use the PROD alias to invoke version 1 of the Lambda function.

Now, you can update the code (the $LATEST version) with all of your improvements, and the npublish another stable and improved version (version 2). You can promote version 2 to production by remapping the PROD alias so that it points to version 2. If you find something wrong, you can easily roll back the production version to version 1 by remapping the PROD alias so that it points to version 1.


## Exam Tips
- Can have multiple versions of Lambda Functions
- Latest version will use $LATEST
- Qualified version will use $LATEST, unqualified will not have it
- Versions are immutable (Cannot be changed)
- Can split traffic using aliases to different versions
    - Cannot split traffic with $LATEST, instead create an alias to latest
    

        
