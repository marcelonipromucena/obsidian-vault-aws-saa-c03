##### Scenario 01
- Company wants to integrate data files from **on-premises with the Cloud** via an **_NFS interface_**
- Which is the **most efficient solution**?
- Answer:
	- Can't be **Storage Gateway - Tape Gateway** since it is used for tape backups with VTL (Virtual Tape Library).
	- Can't be **Storage Gateway - Volume Gateway** since it is used with **_iSCSI_** protocol;
	- Can't be **AWS Site-to-Site VPN** since you cannot use it to integrate data files through NFS interface.
	- <mark style="background: #BBFABBA6;">Storage Gateway - File Gateway is the right answer since it uses the NFS or SMB protocol</mark>

