## Interface Endpoints (Powered by PrivateLink)
- Provisions an **ENI (Private IP address)** as an entry point;
- Must attach a **Security Group**;
- <mark class="hltr-green">Supports most AWS services;</mark>
- Preferred when access is required from on-premises (**Site-to-Site VPN or Direct Connect**), a different VPC or a different region.

## Gateway Endpoints
- Provisions a **Gateway** and must be used as a <mark class="hltr-green">target in a route table</mark>;
- **Does not use Security Groups**;
- <mark class="hltr-red">Supports both S3 and DynamoDB;</mark>
- <mark class="hltr-orange">For S3, gateway is most likely going to be preferred all the time at the exam.</mark>