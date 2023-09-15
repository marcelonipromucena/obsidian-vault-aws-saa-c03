## Scenario 01
#efs #vpc-peering 
- Company have a spreadsheet;
- Spreadsheet is saved on an **EFS file system** created in **us-east-1** region;
- Wants to share the file with other people in **Asia Pacific and Europe** so they can collaborate; 
- What takes the **last amount of operational overhead**?
- Answer:
	- Can't be **S3** cuz it has alot of **operational overhead** since it doesn't let you edit in place.
	- <mark class="hltr-green">The Spreadsheet in an EFS file system can be accessed in other regions by using an <mark class="hltr-red">inter-region VPC peering connection.</mark></mark>
	- <mark class="hltr-green">In this case, you need VPC Peering because you need to use the EFS file system from <mark class="hltr-red">other regions.</mark></mark>
