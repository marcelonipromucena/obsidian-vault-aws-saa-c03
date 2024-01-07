## Target Tracking Scaling
- Most simple and easy to set-up;
- Example: I want the **average** ASG CPU to stay at around 40%;

## Simple / Step Scaling
- When a CW alarm is triggered.
- Example: CPU > 70%, add 2 units;
- Example: CPU < 30%, remove 1 unit;

## Scheduled Actions
- Anticipate a scaling based on known usage patterns;
- Example: increase the min capacity to 10 at 5pm on Fridays;

