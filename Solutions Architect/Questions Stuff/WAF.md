## Scenario 01
- There are types of rules to limit resources:
	1. **rate-based rule**: <mark style="background: #BBFABBA6;">tracks the rate of the requests</mark> from the source IP address and takes<mark style="background: #BBFABBA6;"> action once the limits are crossed</mark>;
	2. **blanked rate-based rule**: prevents <mark style="background: #BBFABBA6;">source IP address from making excessive requests</mark> to entire applications;
	3. **URI-specific rate-based rule**: prevents IP address from making excessive requests to the <mark style="background: #BBFABBA6;">URI of the application.</mark><mark style="background: #FF5582A6;">It is useful if you gotta protect specific functions of the application such as computationally expensive resources from excessive requests;</mark>
	4. **IP reputation rate-based rule**: prevents <mark style="background: #BBFABBA6;">well-known malicious IP addresses</mark> from making excessive requests to the application;

## Scenario 02
- Company runs a photo-sharing web app that is accessed across **three different countries**;
- Application is deployed on several EC2 instances running behind an **ALB**;
- With new Government Regulations, the company has been asked to block access from **two countries and allow access only from the home country of the company**;
- Which configuration should be used?
- Answers:
	- Can't be **Security group** cuz it can't restrict based on user's geo location;
	- Can't be **Geo Restriction feature on CloudFront in a VPC** cuz CloudFront helps restricting traffic based on the user's geographic location but works from edge locations and **doesn't belong to a VPC**;
	- Can't be **Security group for load balancer** cuz it can't restrict based on user's geo location;
	- <mark class="hltr-green">Configure AWS WAF on the Application Load Balancer in a VPC is the right answer.</mark>
	- <mark class="hltr-green">WAF with your ALB can block requests based on the rules in <mark class="hltr-red">web ACL</mark>.</mark>
	- <mark class="hltr-green">Geographic (Geo) Match Conditions in WAF allows you to use WAF to restrict application access based on the geographic </mark>
	- 