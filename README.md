# lucid_test_task

This stack describes resources explicitly mentioned in the task diagram (), some additional resources enabling communication between them and providing accesses, and finally some resources not required by the task itself, but by some of its components. 

I configured some additional resources which are not mentioned in the task, but required for creating necessary components. These are:
- an additional private subnet with a hardcoded CIDR block (10.1.4.0/24) for creating a DBSubnetGroup required for by an RDS DB instance
- an additional public subnet with a hardcoded CIDR block (10.1.3.0/24) required by Application LB
These subnets are mocks and don't have any functionality within this stack. 
All subnets are configured with hardcoded availability zones values to avoid collision (since both Application LB and DBSubnetGroup require having subnets within at least two availability zones).
Also, I added a DB Master password parameter required for an RDS instance.

For enabling communication between components, I created three security groups, allowing traffic between:
- the outbound internet and the loadbalancer
- the loadbalancer and ec2 instances
- ec2 instances and the DB instance

All security groups are set to allow traffic from/to resources having corresponding security groups associated.

