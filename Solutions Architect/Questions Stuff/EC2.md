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
