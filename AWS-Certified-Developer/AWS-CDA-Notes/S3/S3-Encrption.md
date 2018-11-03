# S3 Encryption
There are two types of encryption for S3 Buckets
 - In Transit (encrypting the data you are sending to and from your buckets)
    - SSL/TLS
    
 - At Rest:
    - Server Side Encryption:
        -S3 Manage Keys - **SSE-S3**
        - AWS Key Managment System, Managed Keys **SSE-KMS**
        - Server Side Encryption with Customer Provided Keys - **SSE-CE**

    - Client Side Encryption
        - You encrypt the files yourself before uploading to S3
    
 ## Enforcing Encryption on S3 Buckets
 - Everytime a file is uploaded to S3, a PUT request is initiated.
 - This is what a PUT request looks like:
 
```
PUT.myFile HTTP/1.1
Host: myBucket.s3.amazonaws.com
Date: Wed,25 Apr 2018
Authorization: authorization string
Content-Type: text/plain
Content-Length: 27364
x-amz-meta-author: Ian
Expect: 100-continue
[27364 bytes of object data]
```

- If the files is to be encrypted at upload time, the **x-amz-server-side-encryption parameter** will be included in the request header
- Two options are currently available:
   - **x-amz-server-side-encryption: AES256** (SSE-S3 - S3 Managed Keys)
   - **x-amz-server-side-encryption: ams:kms** (SSE-KMS - KMS Managed Keys)
   
- When this parameter is included in the header of the PUT request, it tells S3 to encrypt the object at the time of upload, using the specified encryption method
- You can enforce the use of Server Side Encryption by using a Bucket Policy which denies any S3 PUT request which doesn't include the **x-amz-server-side-encryption** parameter in the request header

### Example
The following request te]lls S3 to encrypt the file using SSE-S3 (AES-256) at the time of upload
```
PUT.myFile HTTP/1.1
Host: myBucket.s3.amazonaws.com
Date: Wed,25 Apr 2018
Authorization: authorization string
Content-Type: text/plain
Content-Length: 27364
x-amz-meta-author: Ian
Expect: 100-continue
x-amz-server-side-encryption: AES256
[27364 bytes of object data]
```

# S3 Encryption Exam Tips
- Encryption In-Transit (between your computer and S3 - over the network)
    - SSL/TLS(HTTPS)
    
- Encryption At Rest (server side or client side)
    - Server Side Encryption
        - SSE-S3
        - SSE-KMS
        - SSE-C
    - Client Side Encryption

- If you want to enforce the use of encryption for your files stored in S3, use an S3 Bucket Policy to deny all PUT requests that don't include the x-amz-server-side-encryption parameter in the request header.

