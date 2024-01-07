
## Introduction
- Its a Managed NFS (**Network File System**) that <mark class="hltr-green">can be mounted on many EC2</mark>;
- EFS works with EC2 instances in **Multi-AZ**;
- Highly available;
- Scalable;
- **Expen$ive** (**3x gp2**), pay per use;

## Information
- Uses **NFSv4.1** protocol;
- Uses security group to control access to EFS;
- **Compatible with Linux based AMI (fuck Windows)**;
- Supports encryption at rest using **KMS**;
- **POSIX file system (~Linux)** that has a standard file API;
- File system scales automatically, pay-per-use, no capacity planning.