- To create a failover with healthcheck in Route53:
	1. For Primary resources, create an <mark style="background: #BBFABBA6;">alias record pointing to Application Load Balancer</mark> with ‘<mark style="background: #FF5582A6;">evaluate health check</mark>’ as yes.
	2. For Secondary resources,<mark style="background: #BBFABBA6;"> create health checks</mark> for the web servers in the data centers.
	3. <mark style="background: #FF5582A6;">Create two failover alias records, one for primary and one for secondary resources.</mark>

