## VPC
- VPC Endpoint always takes precedence over NAT Gateway.
- VPCs cannot share the same NAT Gateway.

## EC2
##### Scenario 01
- Company runs **data processing workflow**;
- Takes about **60 minutes to complete**;
- Workflow **can withstand disruptions (resiste a interrupções)**;
- **Can be started and stopped multiple times**;
- Which one is the most cost-effective?
- Answer:
	- Cannot be Lambda (Max Exec. Time = 15min; 20x more expensive than Spot.);
	- Cannot be EC2 On-Demand (More expensive than Spot);
	- Cannot be EC2 Reserved (More expensive than Spot);
	- <mark style="background: #BBFABBA6;">EC2 Spot Instances;</mark>

##### Scenario 02
- Company has a web app running 24/7 in prod;
- Wants to run a clone of the same app in dev for **8 hours**;
- Wants the most cost-optimal solution with the best-fit pricing for EC2;
- Answer:
	- Cannot be **Spot Block** because it runs only for up to 6 hours;
	- Cannot be **Spot** because it isn't reliable for running up to 8 hours. It may be auto terminated before the 8 hour threshold;
	- <mark style="background: #BBFABBA6;">Reserved EC2 for PROD (predictable workload and the cheapest option with up to 72% discount if you buy 3 years) and On-Demand for DEV (pay for the time you use it. 8 hours/day).</mark>

##### Scenario 03
- Company has just created an AWS account;
- Team provisioned **an EC2 instance 1A in _region A_**;
- Team takes a snapshot of the instance 1A;
- Team creates a new AMI in region A from the snapshot;
- AMI is copied to another **_region B_**;
- Team provisions an instance **1B** in **_region B_**;
- What **entities** exist in region B?
- Answer:
	- **1 EC2 instance, 1 AMI and 1 snapshot exist in region B**
	- <mark style="background: #BBFABBA6;">When the new AMI is copied from region A into region B, it automatically creates a snapshot in region B because AMIs are based on the underlying snapshots.</mark>
## S3
- Valid URLs for bucket:
		- https://bucketteste.s3.us-east-1.amazonaws.com
			- https:// **(bucket)** . s3 . **(region)** . amazonaws.com
		- https://s3.us-east-1.amazonaws.com/bucketteste
			- https:// s3 . **(region)** . amazonaws.com/ **(bucket)**
##### Scenario 01
- NASA scientist is trying to upload high-res image to S3;
- Image size is 3GB;
- He is using S3 Transfer Acceleration;
- S3TA did not result in an accelerated transfer;
- How AWS would charge this image transfer?
- Answer:
	- Cannot be any option that says "**AWS charges S3 transfer for the image upload.**"
	- <mark style="background: #BBFABBA6;">AWS won't charge for the image upload, because with S3TA you pay ONLY for transfers that ARE INDEED accelerated.</mark>

##### Scenario 02 - Security
- Company is build an application;
- It will deal with **sensitive health information**;
- Backups of the user data **must be kept encrypted in S3**;
- Company does not want to **provide its own encryption keys**;
- **But** still wants to **maintain an audit trail of when an encryption key _was used and by whom_**;
- Which is the best solution?
- Answer:

## Auto Scaling
- Auto Scaling uses termination policies that determine which amazon EC2 instance to be terminated first.
	1. **Default**:
		1. If you select none, this is the default;
		2. Uses <mark style="background: #BBFABBA6;">Last In First Out (LIFO)</mark>
	2. **NewestInstance**:
		1. Terminate the newest instance in the group;
		2. Useful when you're testing a new launch configuration and don't want to keep it for production;
	3. **OldestInstance**:
		1. Terminate the oldest instance in the group;
		2. Useful when upgrading the instance in ASG to new EC2 instance type;
		3. Replaces instances from the old type to the new type;
	4. **ClosestToNextInstanceHour**:
		1. Terminates the instance that are closest to the next billing hour.
		2. Maximize the use of your instance that have an hourly charge.
		3. EC2 instances may be billed on a per-hour or per-second basis.
	5. **OldestLaunchConfiguration**: 
		1. Terminates the instance that have the oldest launch configuration;
		2. Useful when updating a group and <mark style="background: #FF5582A6;">phasing out</mark> the instances from a previous configuration.
	6. **OldestLaunchTemplate**: 
		1. Terminates the instance that have the oldest launch template;
		2. Instances that use the noncurrent launch template are terminated first;
		3. Followed by instances that use the oldest version of the current launch template;
		4. Useful when updating a group and <mark style="background: #FF5582A6;">phasing out</mark> the instances from a previous configuration;
	7. **AllocationStrategy**:
		1. Terminates instances in the ASG to align the remaining instances to the <mark style="background: #BBFABBA6;">allocation strategy</mark> for the type of instance that is terminating;
		2. Either a **spot** or **on-demand**;
		3. If the allocation strategy in the **spot** is *lowest-price*, you can gradually rebalance the distribution of spot instances across your N lowest priced spot pools;
		4. If the allocation strategy in the **spot** is *capacity-optimized*, you can gradually rebalance the distribution of spot instances across spot pools where there is more available spot capacity.
		5. You can also gradually replace **on-demand** instances of a lower priority type with a higher priority type.

##### Scenario 01
- Company wants to perform some maintenance work on a specific EC2 instance;
- That instance is part of ASG using a **step scaling policy**;
- Team is facing maintenance challenge;
- Every time team deploys a new maintenance patch, the healthcheck status shows as **out of service** for a few minutes;
- Causes ASG to provision another replacement instance immediately;
- Which are the **MOST time/resource efficient steps**;
- Which one you recommend so that **maintenance work can be completed at the earliest**;
- Answer:
	- <mark style="background: #BBFABBA6;">1. Suspend the ReplaceUnhealthy process type;   </mark>
	- <mark style="background: #FF5582A6;">2. Do the Maintenance;</mark>
	- <mark style="background: #FFB86CA6;">3. Once the instance is ready set the instance's health status to healthy;</mark> 
	- <mark style="background: #BBFABBA6;">4. Activate ReplaceUnhealthy process type again;</mark>

## Load Balancer
##### Scenario 01
- Company has set up multiple microservices running on EC2 instances;
- EC2 instances running under **ALB**;
- Team wants to **route traffic** to **multiple back-end services** **based on URL path** of the **HTTP Header**;
- Which ALB feature can be used for this?
	- Can't be **HTTP header-based routing** it can be used to route requests but it is not specific to this scenario;
	- Can't be **Query string parameter-based routing** since the url isn't there, in the query string parameters;
	- Can't be **Host-based routing** because it is used to route traffic based on the Host field of the HTTP header. Can be used to route to **multiple domains**;
	- <mark style="background: #BBFABBA6;">Path-based routing is the right answer. You can route a client request based on the URL path of the HTTP header.</mark>

## WAF
- There are types of rules to limit resources:
	1. **rate-based rule**: <mark style="background: #BBFABBA6;">tracks the rate of the requests</mark> from the source IP address and takes<mark style="background: #BBFABBA6;"> action once the limits are crossed</mark>;
	2. **blanked rate-based rule**: prevents <mark style="background: #BBFABBA6;">source IP address from making excessive requests</mark> to entire applications;
	3. **URI-specific rate-based rule**: prevents IP address from making excessive requests to the <mark style="background: #BBFABBA6;">URI of the application.</mark><mark style="background: #FF5582A6;">It is useful if you gotta protect specific functions of the application such as computationally expensive resources from excessive requests;</mark>
	4. **IP reputation rate-based rule**: prevents <mark style="background: #BBFABBA6;">well-known malicious IP addresses</mark> from making excessive requests to the application;

## Route 53
- To create a failover with healthcheck in Route53:
	1. For Primary resources, create an <mark style="background: #BBFABBA6;">alias record pointing to Application Load Balancer</mark> with ‘<mark style="background: #FF5582A6;">evaluate health check</mark>’ as yes.
	2. For Secondary resources,<mark style="background: #BBFABBA6;"> create health checks</mark> for the web servers in the data centers.
	3. <mark style="background: #FF5582A6;">Create two failover alias records, one for primary and one for secondary resources.</mark>

##  Application Discovery Service
- • Plan migration projects by gathering information about on-premises data centers
- Server utilization data and dependency mapping are important for migrations
- **Agentless Discovery**: 
	- Suited for VMWare hosts.
	- Needs to be deployed on a VM host associated with VMware vCenter;
	- No additional software is required to discover parameters;
	- Agent can collect the required information irrespective of the OS installed on VMs.
- **Agent-based Discovery**:
	- Suitable for collecting data for hosts other than VMware hosts;
	- Agents are deployed on machines having Windows, Linux, Ubuntu, CentOS, SUSE;

## Application Migration Service (MGN)
- Evolution of CloudEndure or AWS Server Migration Service (SMS);
- Lift-and-shift (rehost);
- Supports a wide range of SOs, platforms and **databases**;
- **Does not support PostgreSQL or MySQL/MariaDB**;


## Outposts
- Delivers AWS infrastructure and service to virtually any on-premises or edge location that provides a truly consistent hybrid experience;
- It is a fully-managed solution;

##  RDS
##### Scenario 01
- Requires specialized customization to the underlying **Oracle database as well as its host operating system;**
- Improve the **availability** of the Oracle database layer;
- Minimizing the underlying infrastructure maintenance effort;
	- <mark style="background: #BBFABBA6;">RDS Custom for Oracle</mark>

## Aurora
##### Scenario 01
- Company uses Aurora;
- Entire tech stack is deployed in USA;
- Company has plans to expand to Europe and Asia;
- Needs the **games** table to be accessible globally;
- **But** needs the **users** and **games_played** to be accessible regionally;
- **_Minimal Application Refactoring_**
- Answer:
	- Cannot be Dynamo cuz of "Minimal Application Refactoring";
	- <mark style="background: #BBFABBA6;">Aurora Global Database for GAMES table and Aurora for USERS and GAMES_PLAYED table;</mark>

## DynamoDB
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


## SQS
##### Scenario 01
- Company is using SQS to migrate several core banking applications to the cloud;
- They need **High Availability**;
- They need **Cost Efficiency**;
- They expect a peak rate of about **1000 messages per second** to be processed via **SQS**;
- **Messages MUST BE processed in ORDER**;
- Answer:
	- Can't be **SQS FIFO ONLY** since by default FIFO queues only support up to **_300 messages per second_** and the scenario  requires **1000/s**;
	- Can't be **SQS Standard Queues** since standard queues aren't made to process messages **in order**;
	- Can't be **SQS FIFO queue in batch mode of 2 messages per operation** because batch mode multiplies it **x300**, so it would be only **600 messages/s**
	- <mark style="background: #BBFABBA6;">SQS FIFO queue in batch mode of 4 messages per operation: 300 x 4 = 1200 messages/s more than the peak rate of 1000.</mark>


## Storage Gateway
##### Scenario 01
- Company wants to integrate data files from **on-premises with the Cloud** via an **_NFS interface_**
- Which is the **most efficient solution**?
- Answer:
	- Can't be **Storage Gateway - Tape Gateway** since it is used for tape backups with VTL (Virtual Tape Library).
	- Can't be **Storage Gateway - Volume Gateway** since it is used with **_iSCSI_** protocol;
	- Can't be **AWS Site-to-Site VPN** since you cannot use it to integrate data files through NFS interface.
	- <mark style="background: #BBFABBA6;">Storage Gateway - File Gateway is the right answer since it uses the NFS or SMB protocol</mark>

