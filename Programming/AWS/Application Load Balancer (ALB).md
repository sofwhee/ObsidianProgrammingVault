Elastic Load Balancing automatically distributes your incoming traffic across multiple targets, such as EC2 instances, containers, and IP addresses (in one or more Availability Zones)

It monitors the health of its registered targets, and routes traffic only to the healthy targets.

**Elastic Load Balancing** supports: 
- Application Load Balancers
- Network Load Balancers
- Gateway Load Balancers
- Classic Load Balancers.

## Components

![[Pasted image 20250115140237.png]]

**Load Balancer** 
- Serves as the single point of contact for clients. 
- The load balancer distributes incoming application traffic across multiple targets, such as EC2 instances, in multiple Availability Zones. 
- This increases the availability of your application. 
- You add one or more listeners to your load balancer.
**Listener**
- Checks for connection requests from clients, using the **protocol and port that you configure**.
- The **rules** that you define for a listener determine how the load balancer routes requests to its registered targets.
- Rule: **Priority, Actions, and Conditions**
- When the conditions for a rule are met, then its actions are performed.
**Target Group**
- Routes requests to one or more registered targets, such as EC2 instances, using the **protocol and port number** that you specify.
- You can register a target with **multiple target groups**
- You can configure health checks on a **per target group basis**
- Health checks are performed on all targets registered to a target group that is specified in a listener rule for your load balancer.

## Application Load Balancer overview

An Application Load Balancer functions at the application layer, the seventh layer of the Open Systems Interconnection (OSI) model. After the load balancer receives a request, it evaluates the listener rules in priority order to determine which rule to apply, and then selects a target from the target group for the rule action. You can configure listener rules to route requests to different target groups based on the content of the application traffic. Routing is performed independently for each target group, even when a target is registered with multiple target groups. You can configure the routing algorithm used at the target group level. The default routing algorithm is round robin; alternatively, you can specify the least outstanding requests routing algorithm.

## Stickiness

_Stickiness_ is a term that is used to describe the functionality of a load balancer to repeatedly route traffic from a client to a single destination, instead of balancing the traffic across multiple destinations.

For example, traffic from client A can be continually routed to a specific server, so that server can maintain session state data. If traffic from client A is routed to two distinct servers, each server might be missing important information that’s available to the other server.

Therefore, it’s often necessary to maintain a consistent client connection through a load balancer. There are two types of stickiness: sticky sessions and target group stickiness.

**Sticky sessions** 
- Maintains **local session data** in an Amazon Elastic Compute Cloud (Amazon EC2) instance
- Because the instance can **maintain or cache** the session state information locally, it...
	- Simplifies application architecture
	- Improves application performance
- **Two types** of sticky sessions 
	- application cookies 
	- load balancer cookies

**Target group stickiness**
- In blue/green deployments you might have multiple versions of an application deployed, and you might want the client to continue to use the same version of the application during their session. 
- In this case, you can use target group stickiness to route all communications from the client to the same target group instead of the same EC2 instance.

You can use these two stickiness strategies separately or together.