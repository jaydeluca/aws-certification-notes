# S3 Performance Optimization
S3 is designed to support very high requests rates. However, if your S3 buckets are routinely receiving > 100 PUT/LIST/DELETE or > 300 GET requests per second, then there are some best practice guidelines that will help optimize S3 performance.

The guidance is based on the type of workload you are running:
   - **GET-Intensive Workloads** -use CloudFront content delivery service to get best performance. CloudFront will cache your most frequently accessed objects and will reduce latency for your GET requests
   
  
- **Mixed Request Type Workloads** - a mix of GET, PUT, DELETE GET Bucket) - the key names you use for your objects can impact performance for intensive workloads
- S3 uses the key name to determine which partition an object will be stored in
- The use of sequential key names e.g. names prefixed with a time stamp or alphabetical sequence increases the likelihood of having multiple objects stored on the same partition.
- For heavy workloads this can cause I/0 issues and contention
- By using a random prefex to key names, you can force S3 to distribute your keys across multiple partitions, distributing the I/O workload 
   
## S3 Key Name Example
- The following sequential Key Names are not optimal:
    - mybucket/2018-10-15-15-00-00/cust999999/photo1.jpg
    - mybucket/2018-10-15-15-00-00/cust123456/photo2.jpg
    - mybucket/2018-10-15-15-00-00/cust558611/photo3.jpg

- For optimial performance, introduce some randomness into the key name, e.g. prefix the key name with a 4-character hexidecimal hash:
    - mybucket/**7eh4**-2018-10-15-15-00-00/cust999999/photo1.jpg
    - mybucket/**h25d**-2018-10-15-15-00-00/cust123456/photo2.jpg
    - mybucket/**o3n6**-2018-10-15-15-00-00/cust558611/photo3.jpg
    
- This will force S3 to store all of these objects on different partitions, and reduces the likelihood of I/O contention

## SE Performance Optimization - Exam Tips
- Remember the 2 main approaches to Performance Optimization for S3:
    - GET-Intensive Workloads - Use Cloudfront
    
    - Mixed-Workload - Avoid sequential key names for your S3 objects. Instead, add a random prefix like a hex hash to the key name to prevent multiple objects from being store on the same partition
    

## S3 Performance Updates
- In July 2018, Amazon announced a massive increase in S3 performance

- 2,500 PUT requests per second
- 5,500 GET requests

- This new increased performance negates the previous guidance to randomize your object key names to achieve faster performance

- This means logical and sequential naming patterns can now be used without any performance implication
