#shield #cost-optimization
- Company wants to improve security of AWS resources;
- They enabled **AWS Shield Advanced** across multiple AWS accounts owned by the company;
- Upon analysis, the company figured out that the costs incurred are much higher than expected;
- What could be the cause?
- Answers
	- Can't be **AWS Shield Advanced also covers AWS Shield Standard plan** since AWS Shield Standard plan is enabled by default and has no additional cost.
	- Can't be **AWS Shield Advanced is used for custom servers** since AWS Shield **DOESNT** work outside of AWS;
	- Can't be **Saving plans has not been enabled** since Saving Plans only works in **EC2, Lambda and Fargate** in exchange for a commitment to consistent amount of usage (measured in $/hour) for 1 or 3 year term.
	- <mark class="hltr-green">Consolidated Billing has not been enabled is the right answer.</mark> All AWS accounts should fall under a single consolidated billing for the monthly fee to be charged only once.