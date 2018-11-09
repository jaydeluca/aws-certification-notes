# Introduction to DynamoDB
## What is DynamoDB?
**Amazon DynamoDB is a fast and flexible NoSQL database service for all applications that need consistent, single-digit millisecond latency at any scale. It is a fully managed database and supports both document and key-value data models. Its flexible data model and reliable performance make it a great fit for mobile, web, gaming, ad-tech, IoT, and many other applications.

- Stored on SSD storage
- Spread across 3 geographically distinct data centers
- Choice of 2 consistency models: 
    - Eventual Consistent Reads (default)
    - Strongly Consistent Reads
    
### Eventually Consistent Reads:
- Consitency across all copies of data is usually reached within a second. Repeating a read after a short time should return the updated data. (Best Read Performance)
### Strongly Consistent Reads:
- A strongly consistent read returns a result that reflects all writes that received a successful response prior to the read.

## DynamoDB
DynamoDB is made up of:
- Tables
- Items (Think of a row of data in a table)
- Attributes (Think of a column of data in a table)
- Supports key-value and document data structures
- Key = The name of the data, Value = the data itself
- Documents can be written in JSON, HTML, or XML

## DynamoDB - Primary Keys
- DynamoDB stores and retrieves data base on a Primary Key
- 2 Types of Primary Key:
    - **Partition Key** - unique attribute (e.g. UserID)
        - Value of the Partition key is input to an internal hash function which determines the partition or phsyical location on which the data is stored.
        - If you are using the Partition Key as your Primary Key, then no two items can have the same Partition Key

    - **Composite Key (Parition Key + Sort Key)** - in combination
        - e.g. Same user posting multiple times to a forum
            - Primary Key would be a Composite Key consisting of:
                - Partition Key - User ID
                - Sort Key - Timestamp of the post
                - 2 items may have the same Partition Key, but they must have a different Sort Key
                - All items with the same Partition Key are stored together, then sorted according to the value of the Sort Key
                - Allows you to store multiple items using the same partition key
                
## DynamoDB - Students Table
![Image](https://i.imgur.com/zRpPspO.jpg) 
           
## DynamoDB Access Control
- Authentication and Access control is managed using AWS IAM
- You can create an IAM user within your AWS account which has specific permissions to access and create DynamoDB tables
- You can create an IAM role which enables you to obtain temporary access keys which can be used to access DynamoDB
- You can also use a special **IAM Condition** to restrict user access to only their own records
           

### DynamoDB - IAM Conditions Example
- Imagine a mobile gaming application with millions of users
- Users need to access the high scores for each game they are playing
- Access must be restricted to ensure they cannot view anyone else's data
![Image](https://i.imgur.com/rgIsKzY.png)
- This can be done by adding a **Condition** to an IAM Policy to allow access only to items where the Partition Key value matches their User ID

Example of IAM Policy:
![Image](https://i.imgur.com/EyilaJz.jpg)
       

## DynamoDB - Exam Tips
- Amazon DynamoDB is a low latency NoSQL database
- Consists of Tables, Items and Attributes
- Supports both document and key-value data models
- Supported document formats are JSON, HTML, and XML
- 2 Types of Primary Key - Partition Key and combination of Partition Key + Sort Key (Composite Key)
- 2 Consistency Models: 
    - Strongly Consistent (any writes that occur before the read will be reflect in the read - consistent across all three regions)
    - Eventually Consistent (performance can be better, however it can take up to 1 second for new writes or updates to be reflect in the read)
- Access is controlled using IAM Policies
- Fine grained access control using IAM Condition paramter:
    - **dynamodb:LeadingKeys** to allow users to access only the items where the partition key value matches their user ID
    