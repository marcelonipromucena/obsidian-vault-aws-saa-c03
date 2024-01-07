##### Scenario 01
#kinesis-data-stream #dynamodb
- Company is developing a mobile game that **streams score updates** to a backend processor and then **publishes results on a leaderboard**;
- Needs a solution that can **handle major traffic spikes**, **process the game updates in the order of receipt, store the processed updates in a HA database;**
- Company wants to **minimize management overhead required to maintain the solution**;
- Answer:
	- We can use <mark style="background: #BBFABBA6;">Kinesis Data Stream</mark> to stream data at large scales. 
		- It can capture GBs of data per second from hundreds of thousand sources.
		- Data collected is available in **milliseconds** enabling **real-time analytics**;
		- Kinesis Data Stream provides **ordering of records** as well as the ability to **read and/or replay records in the same order to multiple Kinesis Applications**;
	- We can use <mark style="background: #BBFABBA6;">Lambda</mark> which integrates natively with <mark style="background: #BBFABBA6;">Kinesis Data Stream</mark>.
	- The <mark style="background: #FF5582A6;">polling, checkpointing and error handling complexities are abstracted when you use this native integration.</mark>
	- Then we can save the data in <mark style="background: #BBFABBA6;">DynamoDB</mark> which is a highly available database.

##### Scenario 02
#kinesis-data-stream #real-time
- Company operates thousands of hardware devices like **switches, routers, cables, etc...**;
- **_Real-time_** status data of these devices must be fed into a communications application for notifications;
- At the **same time**, another app needs to **read and analyze the same _real-time_ data**.
- Answer:
	- Can't be **SQS with SES** because SES is used to send-emails and not process stuff;
	- Can't be **SQS with SNS** since SNS is used for sending notifications and it doesn't process real-time data;
	- Can't be **SNS** because the same reason as above;
	- <mark style="background: #BBFABBA6;">Kinesis Data Stream is the right answer.</mark>
		- AWS recommends Kinesis for:
			- **Routing related records to the same record processor**. For example: counting and aggregation are simpler when records for a key are routed to the same record processor.
			- **Ordering of records**. E.g.: transfer log data from app host to the processing host while maintaining the order of logs;
			- **Multiple applications to consume the same stream concurrently;**
			- **Consume records in the same order few hours later.** E.g.: billing and audit app that runs few hours behind eachother. Kinesis stores up to 365 days. 

###### Scenario 03
#kinesis-data-firehose 
- Company mantains seismological data for the last 100 years;
- Data has velocity of **1GB/minute;**
- Company wants to store data with o**nly the most relevant attributes;**
- What would be the most **cost-effective** and **least amount of infra maintenance?**
- Answer:
	- Can't be **Kinesis Data Stream** because shards in kinesis doesn't support that much information (1GB/min = 17MB/s way higher than the 1MB/s of KDS);
	- Can't be **Kinesis Data Analytics** since it cannot **directly** ingest data from the source. Data should come from Kinesis Data Stream or Kinesis Data Firehose.
	- <mark class="hltr-green">Kinesis Data Firehose + Lambda function to filter and transform the incoming stream before the output is dumped on S3 is the right answer.</mark> Kinesis Data Firehose can capture, transform and load streaming data into S3 in **near real-time** and is a fully managed service that **scales to match the throughput of your data and requires no ongoing administration.**



##### Scenario 04
