## Storage Tiers (lifecycle management feature)
- Move files after N days;
- **Standard**: for frequently accessed files;
- **Infrequent Access (EFS-IA)**:  cost to retrieve files, lower price to store. Enable EFS-IA with a Lifecycle Policy;

## Availability and Durability
- **Standard**: Multi-AZ, great for prod;
- **One Zone**: 
	- One AZ;
	- Great for DEV;
	- Backup enabled by default;
	- Compatible with infrequent access IA (EFS One Zone-IA);
- <mark class="hltr-green">OVER 90% IN COST SAVINGS!!!!</mark>

