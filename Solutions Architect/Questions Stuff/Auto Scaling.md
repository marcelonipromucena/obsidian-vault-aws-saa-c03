Auto Scaling uses termination policies that determine which amazon EC2 instance to be terminated first.
	1. **Default**:
		1. If you select none, this is the default;
		2. Uses <mark style="background: #BBFABBA6;">Last In First Out (LIFO)</mark>
	2. **NewestInstance**:
		1. Terminate the newest instance in the group;
		2. Useful when you're testing a new launch configuration and don't want to keep it for production;
	3. **OldestInstance**:
		1. Terminate the oldest instance in the group;
		2. Useful when upgrading the instance in ASG to new EC2 instance type;
		3. Replaces instances from the old type to the new type;
	4. **ClosestToNextInstanceHour**:
		1. Terminates the instance that are closest to the next billing hour.
		2. Maximize the use of your instance that have an hourly charge.
		3. EC2 instances may be billed on a per-hour or per-second basis.
	5. **OldestLaunchConfiguration**: 
		1. Terminates the instance that have the oldest launch configuration;
		2. Useful when updating a group and <mark style="background: #FF5582A6;">phasing out</mark> the instances from a previous configuration.
	6. **OldestLaunchTemplate**: 
		1. Terminates the instance that have the oldest launch template;
		2. Instances that use the noncurrent launch template are terminated first;
		3. Followed by instances that use the oldest version of the current launch template;
		4. Useful when updating a group and <mark style="background: #FF5582A6;">phasing out</mark> the instances from a previous configuration;
	7. **AllocationStrategy**:
		1. Terminates instances in the ASG to align the remaining instances to the <mark style="background: #BBFABBA6;">allocation strategy</mark> for the type of instance that is terminating;
		2. Either a **spot** or **on-demand**;
		3. If the allocation strategy in the **spot** is *lowest-price*, you can gradually rebalance the distribution of spot instances across your N lowest priced spot pools;
		4. If the allocation strategy in the **spot** is *capacity-optimized*, you can gradually rebalance the distribution of spot instances across spot pools where there is more available spot capacity.
		5. You can also gradually replace **on-demand** instances of a lower priority type with a higher priority type.

##### Scenario 01
- Company wants to perform some maintenance work on a specific EC2 instance;
- That instance is part of ASG using a **step scaling policy**;
- Team is facing maintenance challenge;
- Every time team deploys a new maintenance patch, the healthcheck status shows as **out of service** for a few minutes;
- Causes ASG to provision another replacement instance immediately;
- Which are the **MOST time/resource efficient steps**;
- Which one you recommend so that **maintenance work can be completed at the earliest**;
- Answer:
	- <mark style="background: #BBFABBA6;">1. Suspend the ReplaceUnhealthy process type;   </mark>
	- <mark style="background: #FF5582A6;">2. Do the Maintenance;</mark>
	- <mark style="background: #FFB86CA6;">3. Once the instance is ready set the instance's health status to healthy;</mark> 
	- <mark style="background: #BBFABBA6;">4. Activate ReplaceUnhealthy process type again;</mark>


##### Scenario 02
#asg #asg-scaling-policy 
- Company observed application works at its peak performance when the EC2 instances have a **CPU Utilization of about 50%**;
- Application uses EC2 and ASG;
- ALB manages and route requests;
- How to make the application run **near its peak performance?**
- Answer:
	- Can't be **simple/step scaling policy** since both uses <mark style="background: #FF5582A6;">threshold for CW alarms that triggers the scaling process.</mark> They can't be configured to use the target metric for CPU utilization;
	- Can't be **CW alarm** since ASG **cannot** use CW alarm as the source for scale-in or scale-out event;
	- <mark style="background: #BBFABBA6;">target-tracking scaling policy is the right answer since you can select a scaling metric (CPU, memory, etc...) and set a target value. </mark>
	- <mark style="background: #BBFABBA6;">target-tracking creates and manages CW alarms that trigger scaling policies and calculates the scaling adjustment based on the metric and target value</mark>
	- <mark style="background: #BBFABBA6;">target-tracking adds or removes capacity as required <mark style="background: #FF5582A6;">to keep the metric at, or close to</mark> the specified target value.</mark>

##### Scenario 03
#asg #asg-scaling-policy 
- Company initiates several computationally intensive workloads on EC2 instances at a designated hour on the last day of every month.
- Payroll department has noticed a **trend on severe performance lag during this hour**;
- Enrineering team has figured out a solution using **ASG** and making sure that **10 instances are available during this peak usage hour;**
- For normal operations only 2 instances are enough;
- Answers:
	- Can't be **ASG target tracking policy + instance count to 10 at designated hour** cause target-tracking policy cannot be used to trigger a scaling action at a **_certain designated hour_**;
	- Can't be **ASG simple tracking policy + instance count to 10 at designated hour** cause target-tracking policy cannot be used to trigger a scaling action at a **_certain designated hour_**;
	- Can't be **ASG scheduled action + Set min count and max count to 10** since it would always keep 10 instances running;
	- <mark class="hltr-green">ASG scheduled actions to start at designated hour + setting the desired capacity to 10 is the right answer.</mark>
