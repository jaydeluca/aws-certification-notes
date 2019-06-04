# Define Operationally Excellent Architectures
##  CloudWatch
CloudWatch Stores metrics for terminated EC2s and deleted ELBs for 15 months

## Design Principles
1. Perform Operations as Code
2. Anticipate Failure
In order to take advantage of the benefits that Cloud has to offer, It is necessary to align the environment and operations teams so that the team can effectively manage the environment. AWS identifies automating your operations and taking time to predict failures as design principles. The others are not part of the design principles.

## AWS Trusted Adviser
1. Offers advice on Whether there is MFA on the root account, and advice on SGs and what ports have unrestricted access

## Really complicated question that keeps coming up

“To better meet the budgetary, security, and compliance needs, a very large financial enterprise with offices all over the world wishes to consolidate their multitude of AWS accounts. The accounts have organically grown over time and without much structure. The decision has been made to use AWS organization and you have been asked to create a solution design for that. Which of the following proposals are NOT valid?”

* For experimentation, the R&D teams (located in Singapore and Germany) require - baring just a few exceptions - unrestricted access to all AWS services and features - including newly released ones. All other teams and in particular all prod environments, should only have access to AWS services that are approved by corporate governance. You propose to use whitelisting by replacing the FullAWSAccess policy (which is - by default - attached to the root) with an SCP that allows only the more limited, desired set of permissions. For the “R&D” lob OU accounts, you propose to use blacklisting by explicitly specifying the access that is not allowed while all other access is allowed

* To be able to centrally manage and to comply with applicable local laws and regulations, you propose the following setup of nested organizational units under root to align with the corporate structure: i) global corporate ii) region (Americas, Asia, Europe, Africa, Oceania) iii) country (e.g. Australia, Canada, etc.) iv) state (e.g. New South Wales, Ontario, etc.) v) lob (e.g. R&D, HR, marketing, etc.) and vi) environment (e.g. dev, test, qa, prod).

* Because an account can be a member of only one organization at a time, you propose to move the corporate HQ master account from the root to the nested “North Carolina” state OU under root. Now local service control policies as well as global corporate SCPs will be applied to this account.

* To help you enable governance, compliance, and operational and risk auditing of your AWS accounts, you propose to use AWS CloudTrail. A user in a master account can create an organization trail that logs all events for all AWS accounts in that organization. Organization trails are automatically applied to all member accounts in the organization.Selected


OUs can be nested up to five levels deep. The master account of the organization is not affected by any SCPs that are attached either to it or to any root or OU the master account might be in. If you replace the default policy on the root, all accounts in the organization are affected by the restrictions. You cannot add them back at a lower level in the hierarchy because an SCP never grants permissions; it only filters them.