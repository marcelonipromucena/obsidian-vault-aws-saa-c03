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