# Indexes Deepdive
## What is an Index?
In SQL databases, an index is a data structure which allows you to perform fast queries on specific columns in a table. You select the columns that you want included in the index and run your searches on the index -- rather than on the entire dataset.

In DynamoDB, 2 types of Indexes are supported to help speed up your DynamoDB queries:
    - **Local Secondary Index**
    - **Global Secondary Index**

### Local Secondary Index
- Can only be created when your creating your table
- You cannot add, remove, or modify it later
- It has the same Partition Key as your original table
- But a different Sort Key
- Gives you a different view of your data, organised according to an alternative Sort Key
- Any queires based on this Sort Key are much faster using the index than the main table
- e.g. Partition Key: User ID
  // Sort Key: account creation date
  
### Global Secondary Index
- You can create when you create your table, or add it later
- Different Partition Key as well as a Different Sort Key
- Gives a completely different view of the data
- Speeds up any queries relating to this alternative Partition and Sort Key
- e.g. Partition Key: email address // Sort Key: last log-in date



## DynamoDB Indexes - Exam Tips
- Indexes enable fast queries on specific data columns
- Give you a different view of your data, based on alternative Partition/Sort Keys
- Important to understand the differences

| Local Secondary Index | Gloabl Secondary Index |
|:-:|:-:|
| Must be created when you create your table| Can create any time - at table creation or after |
| Sme Partition Keys as your table | Different Partition Key|
| Different Sort Key | Different Sort Key |
