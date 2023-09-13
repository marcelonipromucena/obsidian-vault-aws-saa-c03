##### Scenario 01 - DynamoDB + ElastiCache
- Company is evaluating multiple in-memory data store;
- Ability to power its on-demand **live leaderboard**;
- Requires **high availability, low latency, real-time processing**;
- Answer:
	- Can't be **ONLY** DynamoDB as it isn't in-memory itself;
	- Can't be RDS Aurora as it isn't in-memory itself;
	- Can't be Neptune as it isn't in-memory itself;
	- <mark style="background: #BBFABBA6;">DynamoDB DAX is in-memory; High Available; Low Latency.</mark>
	- <mark style="background: #BBFABBA6;">ElastiCache for Redis is in-memory; High Available; Low Latency.</mark>

##### Scenario 02 - DynamoDB + IAM
- Security incident where a new developer was assigned full access to DynamoDB;
- Developer accidentally **deleted tables in production**;
- **Most effective way to solve this so that do not recur**;
- Answer:
	- Can't **Remove full db access for all users** since it would make the database useless. It is not practical;
	- Can't be **Only root user should have full db access** because as best practice, **_the root user should not access the AWS account to carry out any administrative procedures_**;
	- <mark style="background: #BBFABBA6;">Use Permission Boundary to control MAX PERMISSIONS employees can grant to the IAM principals</mark>;
