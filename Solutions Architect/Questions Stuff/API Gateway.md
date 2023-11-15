## Scenario 01
- Company wants to setup AWS cloud architecture that **throttles** requests in case of **sudden traffic spikes**;
- Company is looking for AWS services that can be used for **buffering** or **throttling** to handle such traffic variations;
- What would you recommend?
	- <mark class="hltr-green">API Gateway for throttling</mark>;
	- <mark class="hltr-green">SQS offers buffering capabilities to smooth out temporary volume spikes without losing messages or increased latency;</mark>
	- <mark class="hltr-green">Kinesis offers buffering;</mark>

## Scenario 02
- Company is building a **multi-tier application** to track the location of its trucks during peak operating hours;
- Company wants these data points to be accessible in real time in its analytics platform via a **REST API**;
- You should build a multi-tier solution to store and retrieve this location data for analysis;
- Answer:
	- Can't be **Quicksight with Redshift** since none of them can be used to build a REST API;
	- Can't be **API Gateway with AWS Lambda** since Lambda can't store and retrieve the location data for analysis;
	- Can't be **Athena with S3** since none of them is capable of serving REST APIs;
	- <mark class="hltr-green">API Gateway + Kinesis Data Analytics is the right answer. You can build a REST API with API Gateway that handle incoming requests of truck locations and you can send that data to the Kinesis Data Analytics application on backend. </mark>

## Scenario 03
- Product team at a company has figured out a market need to support both **stateful and stateless client-server** communications via the APIs developed using its platform;
- Using API Gateway, you need to choose.
- Answer:
	- <mark class="hltr-green">API Gateway creates RESTful APIs that enable <mark class="hltr-yellow">stateless</mark> client-server communication. <mark class="hltr-red">It means that calls can be made independently of one another, and each call contains all of the data necessary to complete itself successfully.</mark></mark>
	- <mark class="hltr-green">API Gateway also creates WebSocket APIs that uses WebSocket protocol which is <mark class="hltr-yellow">stateful</mark>. <mark class="hltr-red">It means that it persists the data between multiple transactions.</mark></mark>

