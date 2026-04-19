# Summary

Amazon EC2 Auto Scaling helps you ensure that you have the correct number of Amazon EC2 instances available to handle the load for your application

You create collections of EC2 instances, called _Auto Scaling groups_.

You can specify the minimum number of instances in each Auto Scaling group, and Amazon EC2 Auto Scaling ensures that your group never goes below this size.

You can specify the maximum number of instances in each Auto Scaling group, and Amazon EC2 Auto Scaling ensures that your group never goes above this size.

If you specify the desired capacity, either when you create the group or at any time thereafter, Amazon EC2 Auto Scaling ensures that your group has this many instances.

If you specify scaling policies, then Amazon EC2 Auto Scaling can launch or terminate instances as demand on your application increases or decreases.

Auto Scaling groups use launch templates (or launch configurations) as configuration templates for their EC2 instances.

For example, the following Auto Scaling group has a minimum size of four instances, a desired capacity of six instances, and a maximum size of twelve instances. The scaling policies that you define adjust the number of instances, within your minimum and maximum number of instances, based on the criteria that you specify.

![[Pasted image 20250115154047.png]]

# Features

**Monitoring the health of running instances**
- Amazon EC2 Auto Scaling automatically monitors the health and availability of your instances EC2 health checks
- Replaces terminated or impaired instances to maintain your desired capacity.
**Custom health checks**
- In addition to the built-in health checks, you can define custom health checks that are specific to your application to verify that it's responding as expected. 
- If an instance fails your custom health check, it's automatically replaced to maintain your desired capacity.
**Balancing capacity across Availability Zones**
- You can specify multiple Availability Zones for your Auto Scaling group, and Amazon EC2 Auto Scaling balances your instances evenly across the Availability Zones as the group scales. 
- This provides high availability and resiliency by protecting your applications from failures in a single location.
**Multiple instance types and purchase options**
- Within a single Auto Scaling group, you can launch multiple instance types and purchase options (Spot and On-Demand Instances), allowing you to optimize costs through Spot Instance usage.
- You can also take advantage of Reserved Instance and Savings Plan discounts by using them in conjunction with On-Demand Instances in the group.
**Automated replacement of Spot Instances**
- If your group includes Spot Instances, Amazon EC2 Auto Scaling can automatically request replacement Spot capacity if your Spot Instances are interrupted. 
- Through Capacity Rebalancing, Amazon EC2 Auto Scaling can also monitor and proactively replace your Spot Instances that are at an elevated risk of interruption.
**Load balancing**
- You can use Elastic Load Balancing load balancing and health checks to ensure an even distribution of application traffic to your healthy instances. 
- Whenever instances are launched or terminated, Amazon EC2 Auto Scaling automatically registers and deregisters the instances from the load balancer.
**Scalability**
- Amazon EC2 Auto Scaling also provides several ways for you to scale your Auto Scaling groups.
- Using auto scaling allows you to maintain application availability and reduce costs by adding capacity to handle peak loads and removing capacity when demand is lower. 
- You can also manually adjust the size of your Auto Scaling group as needed.
**Instance refresh**
- The instance refresh feature provides a mechanism to update instances in a rolling fashion when you update your AMI or launch template. 
- You can also use a phased approach, known as a canary deployment, to test a new AMI or launch template on a small set of instances before rolling it out to the whole group.
**Lifecycle hooks**
- Lifecycle hooks are useful for defining custom actions that are invoked as new instances launch or before instances are terminated. 
- This feature is particularly useful for building event-driven architectures, but it also helps you manage instances through their lifecycle.
**Support for stateful workloads**
- Lifecycle hooks also offer a mechanism for persisting state on shut down. 
- To ensure continuity for stateful applications, you can also use scale-in protection or custom termination policies to prevent instances with long-running processes from terminating early.