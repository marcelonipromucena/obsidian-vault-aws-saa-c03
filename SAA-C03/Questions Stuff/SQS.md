## Scenario 01
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


## Scenario 02
#sqs #dynamodb #lambda 
- Company is building a new car-as-a-sensor service by using **fully serverless components**;
- Company does not want to provision the capacity manually;
- Company does not want to respond manually to changing volumes of sensor data;
- What would be the best to do?
- Answer:
	- Can't be **Kinesis Data Firehose, which directly writes the data into an auto-scaled DynamoDB table** because **Kinesis Firehose** cannot write directly to DynamoDB;
	- Can't be any question that says anything about **EC2** since EC2 is **not serverless**;
	- <mark class="hltr-green">Send the data to SQS Standard Queue, which is polled by a Lambda function in batches and the data is written into a DynamoDB;</mark>
	- 