# Scan vs Query API Call
## What is a Query?
- A **Query** operation finds items in a table based on the Primary Key attribute and a distinct value to search for
    - e.g. select an item where the user id is equal to 212, will select all the attributes for that item, e.g. first name, last name, email. etc.

- Use an optional Sort Key name and value to refine the results
    - e.g. if your Sort Key is a timestamp, you can refine the query to only select items with a timestamp of the last 7 days
- By default, a Query returns ll attributes for the items but you can use the **ProjectionExpression** parameter if you want the query to only return the specific attributes you want
    - e.g. if you only want to see the email address rather than all the attributes

- Results are always sorted by the Sort Key
- Numeric Order - by default in ascending order (1,2,3,4)
- ASCII character code values
- You can reverse the order by setting the **ScanIndexForward parameter** to false
- By default, Queries are Eventually Consistent
- You need to explicitly set the query to be Strongly Consistent

## Whsy is a Scan?
- A **scan** operation examines every item in the table
- By default returns all data attributes
- Use the **ProjectionExpression** parameter to refine the scan to only return the attributes you want


![Image](https://i.imgur.com/yRzoEj5.png)
   
## Query or Scan?
- Query is more efficient than a Scan
- Scan dumps the entire table, then filters out the values to provide the desired result - removing the unwanted data
- This adds an extra step of removing the data you don't want
- As the table grows, the scan operation takes longer
- Scan operation on a large table can use up the provisioned throughput for a large table in just a single operation

## How to Improve Performance
- You can reduce the impact of a query or scan by setting a smaller page size which uses fewer read operations
    - e.g. set the page size to return 40 items
- Large number of smaller operations will allow other requests to succeed without throttling
- Avoid using scan operations if you can: design tables in a way that you can use the Query, Get, or BatchGetItem APIs

- By default. a scan operation processes data sequentially in returning 1MB increments before moving on to retrieve the next 1MB of data. It can only scan one partition at a time
- You can configure DynamoDB to use Parallel scans instead by logically dividing a table or index into segments and scanning each segment in parallel
- Best to avoid parallel scans if your table or index is already incurring heavy read/write activity from other applications

## Scan vs Queries - Exam Tips
- A query operation finds items in a table using **only** the **primary key** attribute
    - You provide the Primary Key name and a distinct value to search for
- A **Scan** operation examines **every** item in the table
    - By default returns all data attributes
    - Use the **ProjectionExpression** parameter to refine the results
    
    
- Query results are always sorted by the Sort Key if there is one
- Sorted in Ascending order
- Set ScanIndexForward parameter to false to reverse the order - queries only
- Query operation is generally more efficient then a Scan

- Reduce the impact of a query or scan by setting a smaller page size which uses fewer read operations
- Isolate scan operations to specific tables and segregate them from your mission-critical traffic
- Try parallel scans, rather than the default sequential scan
- Avoid using scan operations if you can: design tables in a way that you can use the Query, Get, or BatchGetItem APIs


   
   