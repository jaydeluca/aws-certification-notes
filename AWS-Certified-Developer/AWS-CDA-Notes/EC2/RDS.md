# RDS

Amazon Relational Database Service

### What is a relational database?
- Database
- Tables
- Row
- Fields (Columns)

| ID | First Name | Surname | Gender |
|:-:|:-:|:-:|:-:|
| 1 | Ian | Arsenault | M |
| 2 | Jay | Deluca | M |
| 3 | Mike | Dobachesky | M |
| 4 | Jameson | Arsenault | M |

## Relational Database Types
- SQL Server
- Oracle
- MySQL Server
- PostgreSQL
- Aurora
- MariaDB

## Non-Relational Databases
- Database
    - Collection       = Table
    - Document         = Row
    - Key Value Pairs  = Fields

```js
{
    "id": "5099803df3f4948bd2f98391",
    "firstname": "Ian",
    "surname": "Arsenault",
    "age": 53
    "address": [
        {
            "street" : "123 Nunya Blvd",
            "city": "Providence",
            "zipcode": 02903
        }
    ]
}
```

## Data Warehousing
Used for business intelligence. Tools like Cognos, Jaspersoft, SQL Server Reporting Services, Oracle Hyperion, and SAP NetWeaver.

Used to pull in very large and complex data sets. Usuaully used by management to do queries on data (such as current performance vs targets, etc.)

## OLTP vs OLAP
Online Transaction Processing (OLTP) differs from OLAP Online Analytics Processing (OLAP) in terms of the types of queries you will run

- OLTP will be simple transactions that happen frequently
- OLAP will be much more complex transactions that will happen infrequently

### OLTP
Example: 
    Order number 215342534
    - Puls up a row of data such as Name, Date, Address to deliver to, Delivery Status, etc.
    
### OLAP
Example:
Net Profit for EMEA and Pacific for the Digital Radio Product.
Pulls in large numbers of records

Sum of Radios sold in EMEA
Sum of Radios sold in Pacific
Unit Cost of Radio in each region
Sales price of each radio
Sales price - unit cost

Data Warehousing databases use different type of architecture both from a database perspective and infrastructure layer.


## Elasticache
Elasticache is a web service that makes it easy to deploy, operate, and scale an in-memory cache in the cloud. The service improves the performance of web applications by allowing you to retrieve information from fast, managed, in-memory caches, instead of relying entirely on slower disk-based databases.

ElastiCache supports two open-source in-memory caching engines:
- Memcached
- Redis

Example: Caching top 10 items on your store in ElastiCache so your production database isn't being hit constantly for top items

## Summary
- RDS - OLTP
    - SQL
    - MySQL
    - Oracle
    - PostgreSQL
    - Aurora
    - MariaDB
- DynamoDNB - No SQL
- Redshift - OLAP
- ElastiCache - In Memory Caching:
    - Memcached
    - Redis
    
    
## Backups, MULTI-AZ & Read Replicas
- There are two different types of Backups for AWS: Automated Backups and Database Snapshots
- **Automated Backups** allow you to recover your database to any point in time within a "retention period". The retention period can be between one and 35 days. Automated backups will take a full daily snapshot and will also store transaction logs throughout the day. When you do a recovery, AWS will first choose the most recent daily backup, and then apply transaction log relevant to that day. This allows you to do a point in time recovery down to a second, within a retention period.
    - enabled by default
    - if RDS instance is 10GB, you will get 10GB worth of storage
    - Backups are taken within a defined window
- **DB Snapshots** are done manually (ie they are user initiated) They are stored even after you delete the original RDS instance, unlike automated backups.


### Restoring Backups
- Whenever you restore either an Automatic Backup or manual snapshot, the restored version of the database will be a new RDS instace with a new DNS endpoint

### Encryption
- Encryption at rest is supported for MySQL, Oracle, SQL Server, PostgreSQL, MariaDB & Aurora. 
- Encryption is done using the AWS Key Management Services (KMS). 
- Once your RDS is encrypted the data stored at rest in the underlying storage is encrypted, as are its automated backups, read replicas, and snapshots.  
- At the present time, encrypting an existing DB instance is not supported. To use Amazon RDS encryption for an existing database, you must first create a snapshot, make a copy of that snapshot and encrypt the copy.

**Important to note for Exam:**
To deploy a encrypted copy of snapshot
- Check off your Snapshot > Actions > Copy Snapshot
- Scroll down to Encryption
- Enable Encryption
- From this we can create a copy and deploy a new RDS instance

## Multi-AZ
- Multi-AZ allows you to have an exact copy of your production database in another Availability Zone. AWS Handles the replication for you, so when your production database is written to, this write will automatically be synchronized to the stand-by database
- In the event of planned database maintenance, DB Instance failure, or an Availability Zone failure, Amazon RDS will automatically failover to the standby so that database operations can resume quickly without administrative intervention.

### What is Multi-AZ RDS?
- **Multi-AZ is for Disaster Recovery only**
- It is not primarily used for improving performance. For performance improvement, you need Read Replicas


## Read Replica
Read replicas allow you to have a read-only copy of your production database. This is achieved by using Asynchronous replication from the primary RDS instance to the read replica. You use read replicas primarily for very read-heavy database workloads.

### Read Replica Databases
- MySQL
- PostgreSQL
- MariaDB
- Auroro
- NOT AVAILABLE FOR SQL SERVER OR ORACLE

------------

- Used for scaling, **NOT** for DR!
- Must have automatic backups turned on in order to deploy a read replica
- You can have up to 5 read replica copies of any database
- You can have read replicas of read replicas (but watch out for latency)
- Each read replica will have its own DNS endpoint
- You **can** have read replicas that have Mutli-AZ
- Read replicas can be promoted to be their own databases. This breaks the replication.
- You can have a read replica in another region

## Exam Tips
- Know the difference between Read Replicas an Multi-AZ
- Read replicas are for scaling, for performance enhancement
- Multi-AZ is for disaster recovery