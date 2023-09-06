## Amazon VPC
- VPC Endpoint always takes precedence over NAT Gateway.
- VPCs cannot share the same NAT Gateway.



## Amazon S3
- Valid URLs for bucket:
		- https://bucketteste.s3.us-east-1.amazonaws.com
			- https:// **(bucket)** . s3 . **(region)** . amazonaws.com
		- https://s3.us-east-1.amazonaws.com/bucketteste
			- https:// s3 . **(region)** . amazonaws.com/ **(bucket)**



## AWS Auto Scaling
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

## AWS WAF
- There are types of rules to limit resources:
	1. **rate-based rule**: <mark style="background: #BBFABBA6;">tracks the rate of the requests</mark> from the source IP address and takes<mark style="background: #BBFABBA6;"> action once the limits are crossed</mark>;
	2. **blanked rate-based rule**: prevents <mark style="background: #BBFABBA6;">source IP address from making excessive requests</mark> to entire applications;
	3. **URI-specific rate-based rule**: prevents IP address from making excessive requests to the <mark style="background: #BBFABBA6;">URI of the application.</mark><mark style="background: #FF5582A6;">It is useful if you gotta protect specific functions of the application such as computationally expensive resources from excessive requests;</mark>
	4. **IP reputation rate-based rule**: prevents <mark style="background: #BBFABBA6;">well-known malicious IP addresses</mark> from making excessive requests to the application;

## Amazon Route 53
- To create a failover with healthcheck in Route53:
	1. For Primary resources, create an <mark style="background: #BBFABBA6;">alias record pointing to Application Load Balancer</mark> with ‘<mark style="background: #FF5582A6;">evaluate health check</mark>’ as yes.
	2. For Secondary resources,<mark style="background: #BBFABBA6;"> create health checks</mark> for the web servers in the data centers.
	3. <mark style="background: #FF5582A6;">Create two failover alias records, one for primary and one for secondary resources.</mark>

## Amazon Application Discovery Service
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

## Amazon Application Migration Service (MGN)
- Evolution of CloudEndure or AWS Server Migration Service (SMS);
- Lift-and-shift (rehost);
- Supports a wide range of SOs, platforms and **databases**;
- **Does not support PostgreSQL or MySQL/MariaDB**;


### AWS Outposts
- Delivers AWS infrastructure and service to virtually any on-premises or edge location that provides a truly consistent hybrid experience;
- It is a fully-managed solution;
- 