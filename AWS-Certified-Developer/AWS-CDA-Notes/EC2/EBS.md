# EBS
Elastic Block Storage  
- Storage volumes in the cloud

## What is EBS?
Amazon EBS (Elastic Block Storage) allows you to create storage volumes and attach them to Amazon EC2 instances. Once attached, you can create a file system on top of these volumes, run a database, or use them in any other way you use a block device.

  
## EBS Volume Types

### SSD
**General Purpose SSD (GP2)**
- General purpose, balances both price and performance
- Ratio of 3 IOS per GB with up to 10,000 IOPS and the ability to burst up to 3000 IOPS for extended periods of time for volumes at 3334 GiB and above.  
  
**Provisioned IOS SSD (IO1)**  
- Designed for I/O intensive applications such as large relational or NoSQL databases
- Use if you need more than 10,000 IOPS
- Can provision up to 20,000 IOPS per volume
  
### Magnetic
**Throughput Optimized HDD (ST1)**  
- Low cost HDD volume designed for frequently accessed, throughput-intensive workloads
- Big data
- Data warehouses
- Log processing
- Cannot be a boot volume
  
**Cold HDD (SC1)**  
- Lowest cost storage for infrequently accessed workloads
- File server
- Cannot be a boot volume
  
**Magnetic (Standard)**  
- Lowest cost per gigabyte of all EBS volume types that is bootable. Magnetic volumes are ideal for workloads where data is accessed infrequently, and applications where the lowest storage cost is important
- Data is accessed infrequently 
- Dev environment testing/setup


## Encrypting EBS Volumnes
- **Volumes that are created from encrypted snapshots are automatically encrypted, and volumes that are created from unencrypted snapshots are automatically unencrypted. If no snapshot is selected, you can choose to encrypt the volume.**