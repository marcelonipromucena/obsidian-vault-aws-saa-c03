## Introduction
- AWS managed NAT
- Higher Bandwidth
- High Available
- No administration
- **Can't be used by EC2 instance in the same subnet (only from other subnets)**
- **Requires an IGW** (<mark class="hltr-green">Private Subnet</mark> -> <mark class="hltr-red">NATGW</mark> -> <mark class="hltr-orange">IGW</mark>)
- <mark class="hltr-green">5 Gbps</mark> of bandwidth 
- Scales up to <mark class="hltr-green">100 Gbps</mark>
- <mark class="hltr-orange">No Security Group is required to manage.</mark>

