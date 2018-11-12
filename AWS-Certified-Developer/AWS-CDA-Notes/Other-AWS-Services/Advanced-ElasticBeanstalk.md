# Advanced Elastic Beanstalk
## Configure Elastic Beanstalk
You can customize your Elastic Beanstalk environment using Elastic Beanstalk configuration files. (e.g. you can define packages to install, create Linux users and groups, run shell commands, specify services to enable or configure your load balancer, etc.)

These are files written in YAML or JSON format. They can have a filename of your choice but you must have a .config extension and be saved inside a folder called **.ebextensions**

## Location of Configuration Files
The **.ebextensions** folder must be included in the top-level directory of your application source code bundle.

This means that the configuration files can be placed under source control along with the rest of your application code

![Image](https://i.imgur.com/KPJaorl.jpg)

## Advanced Elastic Beanstalk - Exam Tips
- You can customize your Elastic Beanstalk environment by adding configuration files
- The files are written in YAML or JSON
- Files have a .config extension
- The .config files are saved to the .ebextensions folder
- Your .ebextensions folder must be located in the top level directory of your application source code bundle



