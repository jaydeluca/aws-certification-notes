# ElastiCache
## What is ElastiCache
- **ElastiCache** - in memory cache in the cloud
- Improves performance of web applications, allowing you to retrieve information from fast in-memory caches rather than slower disk based databases
- Sits between your application and the database:
    - e.g. an application frequently requesting specific product information for your best selling products
- Takes the load off your database
- Good if your databases is particularly read-heavy and the data is not changing frequently

## ElastiCache Benefits and Use Cases
- Improves performance for read-heavy workloads
    - e.g. Social Networking, gaming media sharing, Q&A portals
- Frequently-accessed data is stored in memory for low-latency access, improving the overall performance of your application
- Also good for compute heavy workloads
    - e.g. recommendation engines
- Cna be used to store results of I/O intensive database queries or output of compute-intensive calculations

## 2 Types of ElastiCache
- **Memcached**
    - Widely adopted memory object caching system
    - Mult-threaded
    - No Mutli-AZ capability
- **Redis**
    - Open-source in-memory key-value store
    - Supports more complex data structures: sorted sets and lists
    - Supports Master/Slave replication and Multi-AZ for cross AZ redundancy
    
## Caching Strategies

Two types of strategies available:
    - Lazy Loading
    - Write-Through
    
- **Lazuy Loading** - Loads the data into the cache only when necessary
- If requested data is in the cache, ElastiCache returns the data to the application
- If the data is not in the cache or has expired, ElastiCache returns NULL
- Your application then fetches the data from the database and writes the data received into the cache so that it is available next time

![Image](https://i.imgur.com/yneplHB.jpg)


## Lazy Loading and TTL
- **TTOL (Time To Live)**
    - Specifies the number of seconds until the key (data) expires to avoid keeping stale data in the cache
    - Lazy Loading treats an expired key as a cache miss and causes the application to retrieve the data from the database and subsequently write the data into the cache with a new TTL
    - Does not eliminate stale data - but helps to avoid it


## Write-Through Advantages and Disadvantages
- **Write Through** - adds or updates data to the cache whenever data is written to the database

![Image](https://i.imgur.com/WkuQ2re.jpg?1)



## ElastiCache - Exam Tips
- In Memory Cache that sits between your application and database
- 2 different caching strategies: Lazy Loading and Write Through
- Lazy Loading only caches the data when it is requested
- ElastiCache Node failures not fatal, just lost of cache misses
- Cache miss penalty: Initial request,query database, writing to cache
- Avoid stale data by implementing a TTL
- Write Through strategy writes data into the cache whenever there is a change to the database
- Data is never stale
- Write penalty: Each write involves a write to the cache
- ElastiCache node failure means that data is missing until added or updated in the database
- Wasted resources if most of the data is never used



