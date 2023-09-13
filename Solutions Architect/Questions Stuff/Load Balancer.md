##### Scenario 01
- Company has set up multiple microservices running on EC2 instances;
- EC2 instances running under **ALB**;
- Team wants to **route traffic** to **multiple back-end services** **based on URL path** of the **HTTP Header**;
- Which ALB feature can be used for this?
	- Can't be **HTTP header-based routing** it can be used to route requests but it is not specific to this scenario;
	- Can't be **Query string parameter-based routing** since the url isn't there, in the query string parameters;
	- Can't be **Host-based routing** because it is used to route traffic based on the Host field of the HTTP header. Can be used to route to **multiple domains**;
	- <mark style="background: #BBFABBA6;">Path-based routing is the right answer. You can route a client request based on the URL path of the HTTP header.</mark>

