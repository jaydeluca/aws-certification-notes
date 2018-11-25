# Inline Policies vs Mnaaged Policies vs Custom Policies
## Advanced IAM Policies
Identity Access Management (IAM) is used to define user access permissions within AWS

There are 3 different tpyes of IAM policies available:
- Managed Policies
- Customer Managed Policies
- Inline Policies

## Managed Policies
A **Managed Policy** is an IAM policy which is created and administered by AWS

AWS provide Managed Policies for common use cases based on job function. e.g. AmazonDynamoDBFullAccess, AWSCodePermitPowerUser, AmazonEC2ReadOnlyAccess etc.

These AWS-provided policies allow you to assign appropriate permissions to your users, groups and roles without have to write the policy yourself.

A single Managed Policy can be attached to multiple users, groups, or roles within the same AWS account and across different accounts

You cannot change the permissions defined in an AWS Managed Policy

## Customer Managed Policies
A **Customer Managed Policy** is a standalone policy that you create and administer inside your own AWS account. You can attach this policy to multiple users, groups, and roles - but only within your own account.

In order to create  Customer Managed Policy, you can copy and existing AWS Managed Policy and customize it to fit the requirements of your organization.

Recommended for use cases where the existing AWS Managed Policies don't meet the needs for your environment.

## Inline Policies
An **Inline Policy** is an IAM policy which is actually embedded within the user, group, or role to which it applies. There is a strict 1:1 relationship between the entity and the policy.

When you delete the user, group, or role in which the Inline policy is embedded, the policy will also be deleted.

In most cases, AWS recommends using Managed Policies over Inline Policies.

Inline Policies are useful when you want to be sure that the permissions in a policy are not inadvertently assigned to any other user, group, or role than the one for which they're intended. (i.e. you are creating a policy that must only ever be attached to a single user, group, or role.)

## Advanced Policies - Exam Tips
- Remember the 3 different types of IAM policies:
    - Managed Policy - AWS Managed default policies
    - Customer Managed Policy - Managed By You
    - Inline Policy - Managed by you and embedded in a single user, group, or role
    
- In most cases, AWS recommends using Managed Policies over Inline Policies



