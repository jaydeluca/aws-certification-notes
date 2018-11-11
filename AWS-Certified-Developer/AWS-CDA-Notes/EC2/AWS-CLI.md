# AWS CLI
  
## CLI Tips
- **Least Privilege** - Always give your users the minimum amount of access required
- **Create Groups** - assign your users to groups. Your users will automatically inherit the permissions of the group. The groups permissions are assigned using policy documents

- **Secret Access Key** - You will only see this once If you do not have it you can delete the Key Pair (Access Key ID and Secret Access Key) and regenerate it. You will need to run `aws configure` again.
- **Do not use just one access key** - Do not create just one access key and share that will all your developers. If someone leaves the company on bad terms, then you will need to delete the key and create a new one and every developer will need to update their keys. Instead create one key pair per developer
- **You can use the CLI on your PC** - You can install the CLI on your Mac, Linux of Windows PC. 