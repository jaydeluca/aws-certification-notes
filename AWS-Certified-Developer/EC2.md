# EC2 
Amazon Elastic Compute Cloud (Amazon EC2) is a web service that provides resizable counter capacity in the cloud. 

### Pricing Models
- **On Demand** - allows you to pay a fixed rate by the hour (or by the second) with no commitment
- **Reserved** - provides you with a capacity reservation, and offer a significant discount on the hourly charge for an instance 1 - 3 Terms
- **Spot** - enables you to bid whatever price you want for an instance capacity, providing for even greater savings if your applications have flexible start and end times.
- **Dedicated Hosts** - Physical EC2 server dedicated for your use. Dedicated Hosts can help you reduce costs by allowing you to use your existing server-bound software licenses.

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


##### If a Spot instance is terminated by Amazon EC2, you will not be charged for a partial hour of usage. However, if you terminate the instance yourself, you will be charged for the complete hour in which the instance ran


### EC2 Instance Types
How to remember them:

**FIGHT DR MC PX!**

- **F** for FPGA
- **I** for IOPS
- **G** - Graphics
- **H** - High Disk Throughput
- **T** cheap general purpose (think T2 micro)
- **D** for Density
- **R** for Ram
- **M** - main choice for general purpose apps
- **C** for Compute
- **P**  - Graphics (think Pics)
- **X** - Extreme Memory

What is EBS?
Amazon EBS (Elastic Block Storage) allows yo to create storage volumes and attach them to Amazon EC2 instances. Once attached, you can create a file system on top of these volumes, run a database, or use them in any other way you use a block device.

EBS Volume Types
### SSD
- **General Purpose SSD (GP2)** - balances price and performance for a wide variety of workloads
-  **Provisioned IOPS SSD (IO1)** - highest-performance SSD volumes for mission critical low-latency or high-throughput workloads
	- DESIGNED for I/O intensive applications such as large scale relational db or NOSQL databases
### Magnetic
- **Throughput Optimized HDD (ST1)** - Low cost HDD volume designed for frequently accessed, throughput-intensive workloads
- **Cold HDD (SC1)** - low cost HDD volume designed for less frequently accessed workloads
	- File Server
- **Magnetic (Standard)** - previous generation. Can be a boot volume
	- Data is accessed infrequently 
	- Dev environment testing/setup


