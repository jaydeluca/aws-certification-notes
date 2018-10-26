# IAM
- Manage users and manage level of access to the AWS Console

### IAM Gives you
- Centralized control of your AWS account
- Shared Access to your AWS account
- Granular Permissions
- Identity Federation (LinkedIn, Facebook, AD)
- Multi-factor Authentication
- Temporary access for users/devices and services

### Critical Terms
- Users - End user (think people)
- Groups - Collections of users under one set of permission (Marketing team needs permissions to read certain files in S3 bucket)
- Roles - you create roles and can then assign them AWS resources (used to define a set of permissions, example S3 bucket access - the role can be assumed by either users, AWS services xEC2)
- Policies - document that defines one or more permissions

### What we’ve learned

- IAM Consists of the following:
	- Users
	- Groups ( a way to group our users and apply policies to them collectively)
	- Roles
	- Policy Documents
	- The root account is simply the account created when first setup AWS account. It has complete Admin access
	- New users have no permissions when first crated
	- New users are assigned access key id & secret access keys when first created
	- These are not the same as password, and you cannot use the Access key ID & Secret Access key to login to the AWS Management Console
	- You can use the Access keys via the APIs, and command line.
	- You only get to view the access key and secret access key once. Save them in secure location
	- Always setup multi-factor Authentication on your root account.

