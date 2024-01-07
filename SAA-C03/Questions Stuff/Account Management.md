
## Scenario 01
#root 
- IT consultant is helping the owner of a company to setup an AWS account;
- What are the security recommendations for the **root account**?
- Answers:
	- Can't be **Create AWS account root user access keys and share those keys only with the business owner** because it is not recommended to have an access key for the ROOT account;
	- Can't be **Encrypt the access keys and save them on S3** same as above. IT is not recommended to have an access key for the ROOT account;
	- <mark class="hltr-green">Create a strong password for the AWS account root user</mark> ;
	- <mark class="hltr-green">Enable MFA for the root user account;</mark>

## Scenario 02
- DevOps engineer has joined a large financial service company recently;
- As part of his onboarding, the IT department is conducting a review of the checklists for tasks related to **AWS IAM**;
- Which best practices would you recommend?
- Answers:
	- Can't be **Use user credentials to provide access specific permissions for EC2 instances** since user credentials is not the recommended way of authorizing access to EC2 instances or any resources. Use IAM roles and policies instead;
	- Can't be **Create a minimum number of accounts and share these account credentials among employees**. Thats not the recommended way since sharing credentials could possibly result in a flaw of security. Use IAM roles and policies instead.
	- Can't be **Grant a maximum privileges to avoid assigning privileges again**. It is not recommended since it would void the least-privilege principle.
	- <mark class="hltr-green">Enable MFA for privileged users</mark>;
	- <mark class="hltr-green">Configure AWS CloudTrail to log all IAM actions;</mark>

