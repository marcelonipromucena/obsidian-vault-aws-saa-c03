## Scenario 01
#fsx #fsx-file-gateway #storage
- Company is migrating **on-premises SMB files** to AWS;
- Company has **200TB of data**;
- Should continue to have **low latency access to this data** without any disruption after migration;
- Should have native Windows support;
- Company wants any new application deployed on AWS to have access to this data;
- Which solutions meets this requirement?
- Answer:
	- Can't be **Storage Gateway File Gateway for Amazon S3** since it has no native support for Windows and it is used only to access S3 objects using a file system protocol;
	- Can't be **FSx File Gateway + Applications deployed on AWS can access this data from EFS** since FSx for Windows doesn't support EFS.
	- Can't be **Storage Gateway File Gateway** since it doesn't support file shares for native Windows workload.
	- <mark class="hltr-green">FSx File Gateway + App deployed on AWS can access this data from FSx is the right answer.</mark> 
	- FSx File Gateway provide low-latency, on-premises access to fully managed file shares in FSx for Windows File Server.

## Scenario 02
#fsx #fsx-for-lustre #storage
- Company produces massive volumes of data;
- Data can be divided into two categories: **hot data** and **cold data**;
- **Hot data** needs to be **processed and stored** quickly in a **parallel and distributed way**;
- **Cold data** needs to be kept for reference with **quick access** for **reads** and **updates** at a **low cost**;
- Answers:
	- Can't be **Glue** cuz it is an ETL service and it doesn't store any data;
	- Can't be **FSx for Windows File Server** since it doesn't offer S3 support therefore have no usage for the "cold data" or keeping it at low cost;
	- Can't be **EMR** since EMR doesn't offer storage;
	- <mark class="hltr-green">FSx for Lustre is the right choice</mark> since it can be used to process the hot data in parallel and store the cold data on S3.

## Scenario 03
- Company operates an on-premises data center with hundreds of PB;
- Data is managed on **Microsoft's Distributed File System (DFS)**.
- CTO wants to transition to hybrid cloud and run data-intensive analytic workloads that support DFS;
- Answer:
	- <mark class="hltr-green">FSx for Windows File Server</mark>
- 