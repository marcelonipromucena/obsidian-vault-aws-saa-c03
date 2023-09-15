

## Scenario 01
#guardduty #s3 #ec2
- Company is working to protect data stored in S3 from any malicious activity;
- Also wants to check for vulnerabilities on EC2 instances;
- What would you suggest to address the given requirement?
- Answer:
	- <mark class="hltr-green"><mark class="hltr-red">Amazon GuardDuty</mark> to monitor acitivity on data stored on S3. <mark class="hltr-red">Amazon Inspector</mark> to check for vuln. on EC2 instances.</mark>

## Scenario 02
#guardduty #ec2 #cloudfront #apigateway #rds #load-balancer 
- Company wants to improve security of services they use:
	- EC2;
	- RDS;
	- CloudFront;
	- API Gateway;
	- Elastic Load Balancer;
- People suggested Amazon GuardDuty;
- What **data source** is **supported** by GuardDuty?
- Answer:
	- <mark class="hltr-green">VPC Flow Logs</mark>;
	- <mark class="hltr-green">DNS Logs</mark>;
	- <mark class="hltr-green">CloudTrail events</mark>;

## Scenario 03
#guardduty 
- Company uses GuardDuty;
- Company wants to **stop using GuardDuty**
- What to do?
- Answer:
	- <mark class="hltr-green">Disable the service in the <mark class="hltr-red">general settings</mark></mark>
