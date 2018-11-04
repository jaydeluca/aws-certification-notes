# Cloudfront
### What is a CDN?
A content delivery network (CDN) refers to a geographically distributed group of servers which work together to provide fast delivery of Internet content. A CDN allows for the quick transfer of assets needed for loading Internet content including HTML pages, javascript files, stylesheets, images, and videos. The popularity of CDN services continues to grow, and today the majority of web traffic is served through CDNs, including traffic from major sites like Facebook, Netflix, and Amazon.
- Users farther away will experience more latency

## Edge Location 
- Edge Location is a collection of servers which are in a geographically dispersed data centers, and these edge locations are used in CloudFront to keep a cache of copies of your objects (files, images, etc.) 
- Provides a faster response times
- Dramatically reduces the numbers of hops for your request
- Objects are cached for a period time 

## CloudFront - Key Terminology
- **Edge Location** - This is the location where content is ached and can also be written. Separate to an AWS RegionA/Z
- **Origin** - This is the origin of all the files that the CDN will distribute. Origins can be an S3 Bucket, an EC2 Instance, an Elastic Load Balancer, or Route53
- **Distribution** - This is the name given to the CDN, which consists of a collection of Edge Locations.
    - **Web Distribution** - Typically used for Websties
    - **RTMP** - Used for Media Streaming

CloudFront Distribution Types:
    - **Web Distribution** - Used for Websites, HTTP/HTTPS
    - **RTMP** - (Adobe Real Time Messaging Protocol) Used for Media Streaming/Flash mutli-media content

## What is CloudFront?
Amazon CloudFront can be used to deiver your entire website, including dynamic, static, streaming, and interactive content using a global networking of edge locations. Requests for your content are automaticaly routed to the nearest edge location, so content is delivered with the best possible performance.

e.g. Can be used to optimize performance for users accessing a website backed by S3

## CloudFonrt and S3 Transfer Aceleration
Amazon S3 Transfer Acceleration enables fast, easy, and secure transfer of files over long distances between your end users and an S3 Bucket

Transfer Acceleration takes advantage of Amazon CloudFront's globally distributed edge locations. As the data arrives at an edge location, data is routed to Amazon S3 over an optimized network path.

## CloudFront - Exam Tips
- **Edge Location** - This is the location where content is ached and can also be written. Separate to an AWS RegionA/Z
- **Origin** - This is the origin of all the files that the CDN will distribute. Origins can be an S3 Bucket, an EC2 Instance, an Elastic Load Balancer, or Route53
- **Distribution** - This is the name given to the CDN, which consists of a collection of Edge Locations.
    - **Web Distribution** - Typically used for Websties
    - **RTMP** - Used for Media Streaming
- Edge Locations are not just READ only - you can WRITE to them, too (i.e. PUT an object on them)
- CloudFront Edge Locations are utilised by S3 Transfer Acceleration to reduce latency for S3 uploads.
- Objects are cached for the life of the TTL (Time To Live)
- You can clear cached objects at any time, but you will be charged
- Restrict Viewer Access (Use Signed URL and Signed Cookies) 
    - e.g. paid content
- AWS WAF Web ACL (In Distribution Settings)
    - Traffic filtering for well known attacks like SQL Injection or XSS (protects at application layer)
