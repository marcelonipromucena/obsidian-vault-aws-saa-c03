## Scenario 01
- To create a failover with healthcheck in Route53:
	1. For Primary resources, create an <mark style="background: #BBFABBA6;">alias record pointing to Application Load Balancer</mark> with ‘<mark style="background: #FF5582A6;">evaluate health check</mark>’ as yes.
	2. For Secondary resources,<mark style="background: #BBFABBA6;"> create health checks</mark> for the web servers in the data centers.
	3. <mark style="background: #FF5582A6;">Create two failover alias records, one for primary and one for secondary resources.</mark>

## Scenario 02
#route53 #route53-routing-policies #cloudfront
- Biggest football leagues in Europe has granted the distribution rights for live streaming its matches in the US to a company;
- The company must make sure that **only users from the USA** are able to live stream the matches on their platform;
- Users from other countries in the world must be denied access to these live-streamed matches;
- What do you recommend?
- Answer:
	- Can't be **Route 53 based weighted routing policy** since it would't solve the geo restriction problem;
	- Can't be **Route 53 based failover routing policy** since it would't solve the geo restriction problem;
	- Can't be **Route 53 based latency routing policy** since it would't solve the geo restriction problem;
	- <mark class="hltr-green">Use Georestriction through CloudFront</mark>
	- <mark class="hltr-green">Use Route 53 based geolocation routing policy</mark>
	- 