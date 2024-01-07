## Scenario 01
- Company has a dynamic website <mark class="hltr-green">hosted</mark> **on-premises** in the **USA**;
- Company is launching its website in **Asia**;
- Company wants to optimize the website loading times for new users in **Asia**;
- Website will be launcher in a few days and need it **asap**!
- What do you recommend?
	- Can't be **migrate to S3** since S3 serves static websites, not dynamic ones;
	- Can't be **CloudFront with custom origin pointing to the DNS record of the website on Route 53** since CloudFront cannot have a custom origin pointing to the DNS record of the website on Route 53.
	- Can't be **leverage a Route 53 geo-proximity routing policy poiting to on-premises server** since the on-premises servers continue to be in the US, even using geo-proximity routing policy would direct users in Asia to the on-premise servers in the US and it wouldn't reduce latency.
	- <mark class="hltr-green">Use CloudFront with a custom-origin pointing to the on-premises servers is the right answer.</mark>
	- <mark class="hltr-green">Custom-origins</mark> are any server that **serves content to CloudFront**, **rather than from S3 or other AWS service**. 
	- <mark class="hltr-green">Custom-origins </mark>could be <mark class="hltr-green">any web-server or storage-system </mark>whether it's hosted on AWS or located outside of AWS.

## Scenario 02
- CloudFront offers a multi-tier cache in the form of regional edge caches that improve latency;
- However, there are certain content types that bypass the regional edge cache, and go directly to the origin.
- What are they?
	- <mark class="hltr-green">Proxy methods PUT/POST/PATCH/OPTIONS/DELETE go directly to the origin</mark>
	- <mark class="hltr-green">Dynamic content, as determined at request time (cache-behavior configure to forward all headers.)</mark>

