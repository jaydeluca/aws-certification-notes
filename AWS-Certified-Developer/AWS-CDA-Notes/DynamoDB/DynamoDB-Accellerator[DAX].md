# DynamoDB Accelerator - DAX
## What is DAX?
- **DynamoDB Accelerator (or DAX)** is a fully managed, clustered in-memory cache for DynamoDB
- Delivers up to a 10x read performance improvement
- Microsecond performance for millions of requests per second
- Ideal for Read-Heavy and bursty workloads
    - e.g. auction applications, gaming and retail sites during black Friday promotions
    
## How Does it Work?
- DAX is a write-through caching service - this means data is written to the cache as well as the back end store at the same time
- Allows you to point your DynamoDB API calls at the DAX cluster
- If the item you are querying is in the cache (cache hit), DAX returns the result to the application
- If the item is not available (cache miss) then DAX performs an **Eventually Consistent** GetItem operation against DynamoDB
- Retrieval of data from DAX reduces the read load on DynamoDB tables
- May be able to reduce Provisioned Read Capacity

## What is it NOT Suitable For?
- Caters for Eventually Consistent reads only - so not suitable for applications that require Strongly Consisten reads
- Write intensive applications
- Applications that do not perform many read operations
- Applications that do not require microsecond response times

## DAX - Exam Tips
- DAX provides in-memory caching for DynamoDB tables
- Improves response times for Eventually Consistent reads only
- You point your API calls to the DAX cluster, instead of your table
- If the item you are querying is on the cache, DAX will return it; otherwise it will perform an Eventually Consistent GetItem operation to your DynamoDB table
- Not suitable for write-intensive applications or applications that require Strongly Consistent reads


    
    
    
    