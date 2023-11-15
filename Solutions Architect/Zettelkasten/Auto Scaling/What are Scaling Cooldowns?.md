- After a scaling activity happens, you are in the **cooldown period (default 300s)**
- During the cooldown period, the ASG will not launch or terminate additional instances (to allow for metrics to stabilize)
- <mark class="hltr-green">Advice: </mark> use ready-to-use AMI to reduce configuration time in order to be serving requests faster and reduce the cooldown period.
 