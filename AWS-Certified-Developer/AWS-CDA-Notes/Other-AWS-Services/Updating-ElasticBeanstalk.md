# Updating Elastic Beanstalk
## EBS Deployment Policies
**Elastic Beanstalk** supports several options for porcessing deployments:
   - All at once
   - Rolling
   - Rolling with additional batch
   - Immutable

## All At Once Deployment Policy
All at Once Deployment Updates:
   - Deploys the new version to all instances simultaneously
   - All of your instances are out of service while the deployment takes place
   - You will experience an outage while the deployment is taking place - not ideal for mission-critical production systems
   - If the update fails, you need to roll back the changes by re-deploying the original version to all your instances
    
## Rolling Deployment Policy
Rolling Deployment Updates:
   - Deploys the new version in batches
   - Each batch of instances is taken out of service while the deployment takes place
   - Your environment capacity will be reduced by the number of instances in a batch while the deployment takes place
   - Not ideal for performance sensitive systems 
   - If the upgrade fails, you need to perform an additional rolling update to roll back the changes
    
## Rolling with Additional Batch Deployment Policy
Rolling with Additional Batch Deployment Updates:
   - Launches an additional batch of instances
   - Deploys the new version in batches
   - Maintains full capacity during the deployment process
   - If the update fails, you need to perform an additional rolling update to roll back the changes
   
# Immutable Deployment Policy
Immutable Deployment Updates:
   - Deploys the new version to a fresh group of instances in their own new auto-scaling group
   - When the new instances pass their health checks, they are moved to your existing auto scaling group; and finally, the old instances are terminated
   - Maintains full capacity during the deployment process
   - The impact of a failed update is far less, and the rollback process requires only terminating the new auto scaling group
   - Preferred option for Mission Critical production systems
   
   
   
# Updating Elastic Beanstalk - Exam Tips
- Remember the 4 different deployment approaches:
    - **All at Once**
        - service interruption while you update the entire environment at once
        - To rollback, perform a further All At Once Upgrade
        
    - **Rolling**
        - Reduced capacity during deployment
        - To roll back, perform a further rolling update
        
    - **Rolling with Additional Batch**
        - Maintains full capacity
        - To roll back, perform a further rolling update
        
    - **Immutable**
        - Preferred option for mission critical production systems
        - Maintains full capacity
        - To roll back, just delete the new instances and autoscaling group

    