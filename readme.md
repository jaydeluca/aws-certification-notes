# AWS Developer Associate Certification Notes

We can use this repository as a place to hold notes surrounding the aws developer associate exam. Feel free to break sections into their own files if they get large.


## Iam
- IAM is global, not region-specific
- Users - end users / individuals
- Groups - A collection of users under one set of permissions
- Roles - You create roles and then assign them to AWS resources
- Policies - json document defining one ore more permissions

## EC2
Elastic Compute Cloud (Servers)  
  
### Payment Options

#### On Demand: 
- Pay fixed hourly rate with no commitment
- Good for users that want low cost and flexibility without up-front payment or long term commitment
- Applications with short term, spiky, or unpredictable workloads that cannot be interrupted
- Applications being developed or tested on EC2 for the first time

#### Reserved: 
- Provides you with capacity reservation, and offer a signifcant discount on the hourly charge for an instance. 1 Year or 3 year terms
- Applications with steady state or predictable usage
- Applications that require reserved capacity
- Users can make up-front payments to reduce their total computing costs even further
- Standard RIs (reserved instances) - up to 75% off vs on-demand
- Convertible RIs - up to 54% off vs on-demand
    - Feature the capability to change the attributes of the RI as long as the exchange results in the creation of reserved instances of equal or greater value
- Scheduled RIs are available to launch within the time window you reserve. This option allows you to match your capacity reservation to a predictable recurring schedule that only rquires a fraction of a day, a week, or a month

#### Spot:
- Enables you to big for a price for instance capacity, providing for even greater savings if your applications have flexible start and end times.
- Applications that have flexible start and end times
- Applications that are only feasible at a very low compute prices

#### Dedicated Hosts: 
- Physical EC2 server dedicated for your use. 
- Dedicated hosts can help you reduce costs by allowing you to use your existing server-bound software licenses.
- Useful for regulatory requirements that may not support multi-tenant virtualization
- Great for licensing which does not support multi-tenancy or cloud deployments
- Can be purchased on-demand (hourly)
- Can be purcahsed as a reservation for up to 70% off the on-demand price

### Instance Types
**Fight Dr McPx**  
  
F for FPGA (genomics research, financial analytics, video processing, big data)  
I for IOPS  
G for Graphics  
H for High Disk throughput  
T cheap general purpose
  
D for Density  
R for RAM  
  
M for Main choice for general purchase apps  
C for Compute  
P graphics (think pics)  
X Extreme Memory  

## EBS
Elastic Block Storage  
- Storage volumes in the cloud
  
### Volume Types
**General Purpose SSD (GP2)**
- General purpose, balances both price and performance
- Ratio of 3 IOS per GB with up to 10,000 IOPS and the ability to burst up to 3000 IOPS for extended periods of time for volumes at 3334 GiB and above.  
  
**Provisioned IOS SSD (IO1)**  
- Designed for I/O intensive applications such as large relational or NoSQL databases
- Use if you need more than 10,000 IOPS
- Can provision up to 20,000 IOPS per volume
  
**Throughput Optimized HDD (ST1)**  
- Big data
- Data warehouses
- Log processing
- Cannot be a boot volume
  
**Cold HDD (SC1)**  
- Lowest cose storage for infrequently accessed workloads
- File server
- Cannot be a boot volume
  
**Magnetic (Standard)**  
- Lowest cost per gigabyte of all EBS volume types that is bootable. Magnetic volumes are ideal for workloads where data is accessed infrequently, and applications where the lowest storage cost is important

## Exam Tips
- Know different payment type options (on demand, reserved etc)
- If a spot instance is terminated by EC2, you will not be charged for a partial hour of usage. If you terminate an instance yourself, you will be charged for the complete hour in which the instance ran.
- Fight Dr McPx
- EBS volume types