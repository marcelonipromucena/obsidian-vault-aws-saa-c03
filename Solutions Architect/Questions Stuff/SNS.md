## Scenario 01
#sns #sqs #lambda
- Company built a notification system for its website using **SNS notifications**;
- Notifications are handled by a **Lambda function** for end-user delivery;
- During the **off-season** the notification systems need to handle about **100 requests per second**;
- During the **peak season** the rate touches about **5000 requests per second** and a significant number of notifications are not being delivered to the end-user;
- What is the **Best** solution for this scenario?
- Answer:
	- Can't be **Team needs to provision more servers running the Lambda service** since Lambda is a serverless, scalable function as a service service;
	- Can't be **Amazon SNS has hit a scalability limit, so the team needs to contact AWS support to raise the account limit** since the SNS dynamically scales itself and you don't need to contact AWS support to raise limits.
	- Can't be **Team needs to provision more servers running the SNS service****** since SNS is a serverless, fully-managed service and cannot provision servers.
	- <mark class="hltr-green">Amazon SNS message deliveries to AWS Lambda have crossed the account concurrency quota for Lambda, so the team needs to contact AWS support to raise the account limit is the right answer. </mark>
	- <mark class="hltr-green">The problem here is the Lambda concurrency quota have been throttled for its limit, so the team needs to raise the limits by contacting AWS.</mark>

