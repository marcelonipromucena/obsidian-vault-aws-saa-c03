route traffic between two VPCs having **overlapping** subnets.

1. Create **new subnets** from **new CIDR** in EACH VPC.
2. Deploy a **private NAT gateway** in **VPC A** and an **Application Load Balancer in VPC B**.
3. Use **Transit Gateway** to route traffic between these VPCs.
4. Update the Route table of the overlapping subnets in VPC A to send all traffic destined to overlapping subnets of VPC B  via a private NAT gateway.
5. Reverse traffic from **VPC B** will communicate through **ALB**. The ALB will use the IP address of the private **NAT gateway** as a destination.
![[overlapping-vpc-cidrs.drawio.png]]