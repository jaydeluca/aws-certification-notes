# Design Performance Architectures
## S3
### Eventual Consistency 
Updates to a single key are atomic. For example, if you PUT to an existing key, a subsequent read might return the old data or the updated data, but it will never return corrupted or partial data.
[Introduction to Amazon S3 - Amazon Simple Storage Service](https://docs.aws.amazon.com/AmazonS3/latest/dev/Introduction.html#ConsistencyModel)

## AMIs
## Autoscaling
AMI ID is specified in the Launch Configuration
[Launch Configurations - Amazon EC2 Auto Scaling](https://docs.aws.amazon.com/autoscaling/ec2/userguide/LaunchConfiguration.html)

