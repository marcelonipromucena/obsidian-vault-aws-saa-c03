## Scenario 01
#aurora #aurora-global-tables
- Company uses Aurora;
- Entire tech stack is deployed in USA;
- Company has plans to expand to Europe and Asia;
- Needs the **games** table to be accessible globally;
- **But** needs the **users** and **games_played** to be accessible regionally;
- **_Minimal Application Refactoring_**
- Answer:
	- Cannot be Dynamo cuz of "Minimal Application Refactoring";
	- <mark style="background: #BBFABBA6;">Aurora Global Database for GAMES table and Aurora for USERS and GAMES_PLAYED table;</mark>

## Scenario 02
#aurora #aurora-multi-az #disaster-recovery #aurora-replica-priority-tier
- Company uses Aurora;
- Company deployed **5 multi-az read replicas**;
- Replicas have been assigned the following **failover priority tiers**;
- tier-1(16TB),tier-1(32TB),tier-10(16TB),tier-15(16TB),tier-15(32TB);
- Answer:
	- <mark style="background: #BBFABBA6;">Tier-1(32TB)</mark>
	- **Each read-replica is associated with a <mark style="background: #BBFABBA6;">Priority Tier</mark> <mark style="background: #ef6c00;">(0-15)</mark>**;
	- In the event of a failover, Aurora will promote the Read Replica that has the highest priority (**lowest numbered tier**)
	- If two or more replicas share the same <mark style="background: #BBFABBA6;">priority</mark>, the largest one in size is promoted;
	- If two or more replicas share the same <mark style="background: #BBFABBA6;">priority and size</mark>, Aurora promotes an **arbitrary replica in the same promotion tier**;

## Scenario 03
- Company manages a **multi-tier** social media application that runs on **EC2** behind **ALB**;
- Instances run in an **ASG** across multiple AZs and uses **Aurora**;
- How to make the application **more resilient to periodic spikes in request rates?**
- Answer:
	- Can't be **AWS Direct Connect** since Direct Connect is used to setup a dedicated link between on-premises and AWS;
	- Can't be **Global Accelerator** since CloudFront is better at improving performance and resiliency for multi-tier applications.
	- Can't be **AWS Shield** since it is used to protect the AWS VPC from DDoS attacks.
	- <mark class="hltr-green">Use Aurora Replicas for more high-availability and as consequence, more resiliency.</mark>
	- <mark class="hltr-green">Use CloudFront distribution in front of the ALB for more content delivery at the edge.</mark>
	- 