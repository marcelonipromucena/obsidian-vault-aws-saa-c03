#ebs #efs 

## EBS
#### EBS volumes
- One instance (except multi-attach io1/io2) 
- Are **locked at the Availability Zone** (AZ) level 
- **gp2**: IO increases if the disk size increases 
- **io1**: can increase IO independently

####  To migrate an EBS volume across AZ
1. Take a snapshot
2. Restore the snapshot to another AZ;
3. **EBS** **backups** **uses IO** and you shouldn't run them while your app is handling a lot of traffic.

**Root EBS Volumes** of instances get terminated by default if the EC2 instance gets terminated. (you can disable that)


## EFS
- Can mount in **100s of instances across AZs.**
- EFS share website files (**Wordpress**);
- Only for **Linux** Instances (**POSIX**);
- **EFS has a higher price point than EBS;**
- Can leverage EFS-IA for cost savings;

### Remember: EFS vs EBS vs Instance Store