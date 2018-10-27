# RDS

Amazon Relational Database Service

### What is a relational database?
- Database
- Tables
- Row
- Fields (Columns)

|| ID || First Name || Surname || Gender ||
| 1 || Ian | Arsenault | M |
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
    
    