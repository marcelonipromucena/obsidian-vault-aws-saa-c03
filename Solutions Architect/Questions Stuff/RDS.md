##### Scenario 01
- Requires specialized customization to the underlying **Oracle database as well as its host operating system;**
- Improve the **availability** of the Oracle database layer;
- Minimizing the underlying infrastructure maintenance effort;
	- <mark style="background: #BBFABBA6;">RDS Custom for Oracle</mark>

##### Scenario 02
- Subject just joined a dev team and wants to understand the replication capabilities for **RDS Multi-AZ** as well as **Read Replicas**;
- What is right about it?
- Answer:
	- <mark style="background: #BBFABBA6;">Multi-AZ has <mark style="background: #FF5582A6;">Synchronous replication</mark> and spans across <mark style="background: #FFB86CA6;">at least two AZs within a Single Region.</mark></mark>
	- <mark style="background: #BBFABBA6;">Read Replicas has <mark style="background: #FF5582A6;">Asynchronous replication</mark> and <mark style="background: #BBFABBA6;">can be within an AZ; Cross-AZ or Cross Region.</mark></mark>
