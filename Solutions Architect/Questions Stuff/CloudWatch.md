## Scenario 01
- Development team noticed that an unusually large number of **illegal AWS API queries were made** sometime during the week;
- Due to off-season there was no visible impact;
- The management wants an automated solution that can trigger **near-real-time** warnings in case such an event recurs;
- Answer:
	- <mark class="hltr-green">1. Create a CloudWatch metric filter that processes CloudTrail logs;</mark>
	- <mark class="hltr-green">2. CloudTrail logs with specific informations like error codes and details are tracked;</mark>
	- <mark class="hltr-green">3. Create an alarm based on this metric's rate to send an SNS notification to the team.</mark>
