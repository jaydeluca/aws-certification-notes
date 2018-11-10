# DynamoDB Provisioned Throughput
## DynamoDB Read and Write Capacity Units
- DynamoDB Provisioned Throughput is measured in Capacity Units
- When you create your table, you specify your requirements in terms of Read Capacity Units and Write Capcity Units
- 1 x Write Capacity Unit = 1 x 1KB Write per second
- 1 x Read Capacity Unit = 1 x Strongly Consistent Read of 4KB per second

    OR
    
  2 x Eventually Consistent Reads of 4KB per second (default)
  
  
## DynamoDB Example Configuration
- Table with 5 x Read Capacity Units and 5 x Write Capacity Units
- This configuration will be able to perform:
    - 5 x 4KB Strongly Consistent reads = 20KB per second
    - Twice as many Eventually Consistent = 40KB
    - 5 x 1KB Writes = 5KB per second
    
- If your application needs reads or writes larger items will consume more Capacity Units and will cost you more as well


## Strongly Consistent Read Calculations  
- Your application needs to read 80 items (table rows) per second
- Each item is 3KB in size
- You need Strongly Consistent Reads

- First, calculate how many Read Capacity Units needed for each read:

    Size of each item / 4KB
    
    3KB/4KB = 0.75
- Rounded-up to the nearest whole number, each read will need 1 x Read Capacity Unit per read operation
- Multiplied by the number of reads per second - 80 Read Capacity Units required

## Eventually Consistent Reads Calculation
- What if you need Eventually Consistent Reads?
- You do the same calculation. However as this is for Eventually Consistent reads and you get 2 x 4KB per second - or **double** the throughput of Strongly Consistent reads

- Size of each item / 4KB
    - 3KB/4KB = 0.75 Round-up to the nearest whole number, = 1
    - Multiply by the number of reads per second = 80
    
- Divide 80 by 2, so you only need 40 Read Capacity Units for Eventually Consistent reads

## Write Capacity Units Calculation
- You want to write 100 items per second
- Each item 512 bytes in size
- First, calculate how many Capacity Units for each write:
    - Size of each item / 1KB (for Write Capacity Units)
    
    512 bytes / 1KB = 0.5
- Rounded-up to the nearest whole number, each write need 1 x Write Capacity Unit per write operation
- Multiplied by the number or writes per second = 100 Write Capacity Units required

## DynamoDB Provisioned Throughput - Exam Tips
- Provisioned Throughput is measured in Capacity Units
- 1 x Write Capacity Unit = 1 x 1KB Write per second
- 1 x Read Capacity Unit = 1 x 4KB Strongly Consistent Read OR 2 x 4KB Eventually Consistent Reads per second



  
  