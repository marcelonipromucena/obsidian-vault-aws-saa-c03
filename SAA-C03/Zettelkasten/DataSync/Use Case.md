
### Question
#data-sync #direct-connect 
- Company has created an **AWS Direct Connect** connection for migrating its application to the AWS Cloud;
- On-premises application writes **hundreds of video files** into a <mark class="hltr-green">mounted NFS file system</mark> daily;
- Post-migration, the company will host the application on an Amazon EC2 instance with a mounted **EFS file system**.
- Before the migration cutover, the company must build a process that will replicate the newly created on-premises video files to the **EFS file system**;

#### Answer

1. **Configure DataSync agent** on the on-premises server that has access to the NFS file system;
2. Transfer data over the **Direct Connect** to Amazon EFS through VPC Endpoint (Private Link) by using a **private VIF**;
3. Setup a DataSync **scheduled task** to send the video files to the EFS file system every 24 hours.
