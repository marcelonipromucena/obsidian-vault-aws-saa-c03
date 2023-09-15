## Scenario 01 
#dynamodb #elasticache
- Company is evaluating multiple in-memory data store;
- Ability to power its on-demand **live leaderboard**;
- Requires **high availability, low latency, real-time processing**;
- Answer:
	- Can't be **ONLY** DynamoDB as it isn't in-memory itself;
	- Can't be RDS Aurora as it isn't in-memory itself;
	- Can't be Neptune as it isn't in-memory itself;
	- <mark style="background: #BBFABBA6;">DynamoDB DAX is in-memory; High Available; Low Latency.</mark>
	- <mark style="background: #BBFABBA6;">ElastiCache for Redis is in-memory; High Available; Low Latency.</mark>

## Scenario 02 
#dynamodb #iam
- Security incident where a new developer was assigned full access to DynamoDB;
- Developer accidentally **deleted tables in production**;
- **Most effective way to solve this so that do not recur**;
- Answer:
	- Can't **Remove full db access for all users** since it would make the database useless. It is not practical;
	- Can't be **Only root user should have full db access** because as best practice, **_the root user should not access the AWS account to carry out any administrative procedures_**;
	- <mark style="background: #BBFABBA6;">Use Permission Boundary to control MAX PERMISSIONS employees can grant to the IAM principals</mark>;

## Scenario 03
#dynamodb #dax #cloudfront #s3
- Company developed a **REST API** which is deployed in an **ASG** using **ALB**;
- API stores the user data in **DynamoDB**;
- Static content is served via S3;
- Analyzing the usage trends, it is found that **90%** of the read requests are for **commonly accessed data** across all users.
- What would you suggest to improve application performance in the **MOST efficient way**?
- Answers:
	- Can't be **Enable DAX and Elasticache Memcached for S3** since Memcached is not for S3;
	- Can't be **ElastiCache Redis for DynamoDB and ElastiCache Memcached for S3** since ElastiCache Redis isn't for DynamoDB and ElastiCache Memcached isn't for S3;
	- Can't be **ElastiCache Redis for DynamoDB and CloudFront for S3** since ElastiCache Redis isn't used in DynamoDB;
	- <mark class="hltr-green">Enable DynamoDB Accelerator (DAX) for DynamoDB and CloudFront for S3 is the right answer since DAX adds a caching layer in Dynamo for reading and CloudFront add caching-on-the-edge for Static content in S3.</mark>

## Scenario 03
#dynamodb #dax #elasticache
- Company uses DynamoDB;
- Some use-cases need high request rate (**millions of requests per second**), **low predictable latency** and **reliability.**;
- Company wants to add a caching layer to support high read volumes;
- What do you recommend?
- Answers:
	- <mark class="hltr-green">ElastiCache</mark>
	- <mark class="hltr-green">DynamoDB Accelerator (DAX)</mark>
