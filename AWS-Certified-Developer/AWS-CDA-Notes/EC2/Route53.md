# Route 53

Route 53 is Amazon’s DNS service

- Allows you to map your domain names to:
	- EC2 instances
	- Load Balancers
	- S3 Buckets
  
- Hosted Zones
	- Like a traditional DNS zone file, a hosted zone represents a collection of resource record sets that are managed together under a single domain name. Each hosted zone has its own metadata and configuration information.

- Zone Apex
	- Sometimes called the "root domain" or "naked domain"
	- roshambo.com as opposed to www.roshambo.com

- Alias
	- Let you route traffic to selected AWS resources, such as CloudFront distributions and Amazon S3 bucket. 
	- Let you route traffic from one record in a hosted zone to another record.