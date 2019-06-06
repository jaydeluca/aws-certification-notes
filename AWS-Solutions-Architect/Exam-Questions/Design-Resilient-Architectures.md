# Design Resilient Architectures
## RDS
### Replication 
Multi-AZ deployments utilize synchronous replication, making database writes concurrently on both the primary and standby so that the standby will be up-to-date in the event a failover occurs.

## SQS
With Standard Queues, each message will be delivered at least once, this ensures that no message is lost, but leaves you t manage duplicates. SQS standard queues will process messages in a loosely sequential order, due to the number of SQS nodes and that some may be restarting or load splitting the order is not guaranteed. You should recognize that all the others are related FiFo queues.
Resources
*  [SQS Product Details](https://aws.amazon.com/sqs/details/) 
*  [How SQS works](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-how-it-works.html) 
*  [How SQS FiFo works (blog)](https://aws.amazon.com/blogs/developer/how-the-amazon-sqs-fifo-api-works/) 

## Load Balancing
### Round Robin Policies
Classic LBS use round robin only for TCP
ALBs use it for final node selection after reading routing rules
NLBs do not use Round Robin Policies
[How Elastic Load Balancing Works - Elastic Load Balancing](https://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/how-elastic-load-balancing-works.html)
## Networking Throughput Issues
A lot of questions are something like “Things are failing because of network”
This is likely due to 2 issues depending on context
1. Undersized Proxy Server
2. Inadequately Provisioned NAT Instance
[AWS Articles](https://aws.amazon.com/articles/high-availability-for-amazon-vpc-nat-instances-an-example/)

## Cross-Region Replication
Parts that get replicated with the actual data
1. Metadata
2. ACLs
[Cross-Region Replication - Amazon Simple Storage Service](https://docs.aws.amazon.com/AmazonS3/latest/dev/crr.html)

## EFS
1. Port 2049
2. Requires Bi-Directional access - 2049 both ways
3. Can be mounted using `mount -t nfs -o xxxx`
4. Can set file permissions with `chmod` and `chown`
 [EFS - How It Works](https://docs.aws.amazon.com/efs/latest/ug/how-it-works.html) 
 [EFS limits](https://docs.aws.amazon.com/efs/latest/ug/limits.html) 
 [EFS Security](https://docs.aws.amazon.com/efs/latest/ug/security-considerations.html) 
 [EFS Security Groups](https://docs.aws.amazon.com/efs/latest/ug/accessing-fs-create-security-groups.html) 
 [Mounting and EFS target](https://docs.aws.amazon.com/efs/latest/ug/wt1-getting-started.html) 
## Multi-AZ
### Services that are multi-AZ by default
1. Neptune
2. DynamoDB
3. S3

