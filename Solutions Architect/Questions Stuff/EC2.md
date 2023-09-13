##### Scenario 01
#ec2 #spot #cost-effective
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
#ec2 #cost-effective #instance-type
- Company has a web app running 24/7 in prod;
- Wants to run a clone of the same app in dev for **8 hours**;
- Wants the most cost-optimal solution with the best-fit pricing for EC2;
- Answer:
	- Cannot be **Spot Block** because it runs only for up to 6 hours;
	- Cannot be **Spot** because it isn't reliable for running up to 8 hours. It may be auto terminated before the 8 hour threshold;
	- <mark style="background: #BBFABBA6;">Reserved EC2 for PROD (predictable workload and the cheapest option with up to 72% discount if you buy 3 years) and On-Demand for DEV (pay for the time you use it. 8 hours/day).</mark>

##### Scenario 03
#ec2 #regions #ami #snapshot
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

##### Scenario 04
#ec2 #storage
- Company is documenting the process flow to provision EC2 instances;
- Instances will be used in internal applications that processes HR payroll data;
- Company wants to highlight those volume types that **_CANNOT_ be used as BOOT VOLUME**;
- Which ones?
- Answer:
	- General Purpose(gp2); Provisioned IOPS SSD (io1) and Instance Store **can** be used as **boot volume**;
	- <mark style="background: #BBFABBA6;">Cold HDD (_sc1_) can't be used;</mark>
	- <mark style="background: #BBFABBA6;">Throughput Optimized HDD (_st1_)</mark>

##### Scenario 05
#ec2 #hpc
- Company is assisting NASA;
- Uses High-Performance Computing (**HPC**) driven application architecture;
- Which **EC2 instance topology** should this application be deployed on?
- Answer:
	- <mark style="background: #BBFABBA6;">EC2 instances should be deployed in Cluster Placement Group to benefit from Low Network Latency and High Network Throughput </mark>
