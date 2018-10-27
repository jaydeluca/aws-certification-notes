# Exam Tips
- Know different payment type options (on demand, reserved etc)
- If a spot instance is terminated by EC2, you will not be charged for a partial hour of usage. If you terminate an instance yourself, you will be charged for the complete hour in which the instance ran.
- Fight Dr McPx
- EBS volume types

### EC2 Encrypt
- You can encrypt root device volume (the volume of OS is installed on) using Operating System level encryption 
- You can encrypt root device volume by first taking a snapshot of that volume, and then creating a copy of that snap with encryption. You can then make an AMI of this snap and deploy the encrypted root device volume
- You can encrypt additional attached volumes using the console, CLI or API