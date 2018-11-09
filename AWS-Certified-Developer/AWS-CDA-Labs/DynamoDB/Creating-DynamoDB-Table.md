# Creating DynamoDB Table
1. Create a new IAM role for EC2
    1. Service role > EC2 > Select Full DynamoDBAccess > Name role > Create Role
2. Create new EC2 instance 
    1. Launch new Linux instance
    2. Select IAM Role 
    3. Add bash script 
    
    ```bash
    #!/bin/bash
    yum update -y
    yum install httpd php git -y
    service httpd start
    chkconfig httpd on
    cd /var/www/html
    echo "<?php phpinfo();?>" > test.php
    git clone https://github.com/acloudguru/dynamodb
    ```
    4. Add tag
    5. Two Security Groups - SSH and HTTP port 80
3. SSH into EC2 instance
```sh 
ssh ec2-user@00.000.00.000 -i my-key-name.pem
```
4. go into /var/www/html directory
```sh 
sudo su
cd /var/www/html
ls
>> dynamodb  test.php
```
5. Install SDK for PHP
```sh 
#Commands to install Composer and PHP SDK

curl -sS https://getcomposer.org/installer | php
php composer.phar require aws/aws-sdk-php
```
6. CD into dynamodb directory
```sh 
cd dynamodb
>> createtables.php  README.md  uploaddata.php
```
7. Update createtables.php and uploaddata.php files to use correct region
```sh 
$client = DynamoDbClient::factory(array(
    'region' => 'us-east-2',  // replace with your desired region visit http://docs.aws.amazon.com/general/latest/gr/rande.html to get your regions.
    'version' => '2012-08-10' // Now needs a version
));
```
8. Take your EC2 instance ip address and go to the following url
- `http://00.000.00.000/dynamodb/createtables.php` will create all tables in dynamodb
- `http://00.000.00.000/dynamodb/uploaddata.php` will upload data to the tables
9. You should now be able to check your tables and data in DynamoDB under Tables

### How to interact with your database using comand line
```sh 
aws dynamodb get-item --table-name ProductCatalog --key '{"Id":{"N":"205"}}'
>> {
       "Item": {
           "BicycleType": {
               "S": "Hybrid"
           }, 
           "Description": {
               "S": "205 Description"
           }, 
           "Title": {
               "S": "20-Bike-205"
           }, 
           "Color": {
               "SS": [
                   "Black", 
                   "Red"
               ]
           }, 
           "Gender": {
               "S": "B"
           }, 
           "Price": {
               "N": "500"
           }, 
           "ProductCategory": {
               "S": "Bicycle"
           }, 
           "Brand": {
               "S": "Brand-Company C"
           }, 
           "Id": {
               "N": "205"
           }
       }
   }

```