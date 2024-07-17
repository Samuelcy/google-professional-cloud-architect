Instance Groups
- Instance Group - Group of VM instances managed as a single entity, manage group of similar VMs having similar lifecycle as one unit
- Two Types of Instance Groups
	- Managed: Identical VMs created using a template:
		- Features: Auto scaling, auto healing and managed releases
	- Unmanaged: different configuration for VMs in same group:
		- Does not offer auto scaling, auto healing & other services
- Location can be zonal or regional

Managed Instance Groups (MIG)
- Managed Instance Group  - Identical VMs created using an instance template
- Maintain certain number of instances
	- If an instance crashes, MIG launches another instance
	-  Detect application failures using health checks (Self Healing)
	- Increase and decrease instances based on load (Auto Scaling)
	- Add load balancer to distribute load
	- Create instances in multiple zones (regional MIGs)
		- Regional MIGs provide higher availability compared to zonal MIGs
	- Release new application versions without downtime
		- Rolling updates: Release new version step by step (gradually). Update a percentage of instances to the new version at a time
		- Canary Deployment: Test new version with a group of instances before releasing it across all instances

Creating Managed Instance Group (MIG)
- Instance template is mandatory
- Configure autoscaling to automatically adjust number of instances based on load:
	- Minimum number of instances
	- Maximum number of instances
	- Autoscaling metrics: CPU utilization target or load balancer utilization target or any other metric from stack driver
		- Cool down period: How long to wait before looking at auto scaling metrics again?
		- Scale in controles: Prevent a sudden drop in no of VM instances
			- Example: Don't scale by more than 10% or 3 instances in 5 mintues
		- Autohealing: Configure a health check with initial delay (How long should yo uwait for your app to initialize before running a health check?)
		  
Updating a Managed Instance Group (MIG)
- Rolling update: Gradual update of instances in an instance group to the new instance template
	- Specify new template:
		- (Optional) specify a template for canary testing
	- Specify how do you want the update to be done
		- When should the update happen?
			- Sstart the update immidately (proactive) or when the instance group is resized latter (opporturistic)
		- How should the update happen?
			- Maximum surge: How many instances are added at any point in time?
			- Maximum unavailable: How many instances can be offline during the update?
- Rolling Restart/replace: Gradual restart or replace of all instances in the group
	- No change in template BUT replace/restart existing VMs
	- Configure Maximum surge, Maximum unavailable and what you want to do?
	  
	  
Question 1:

V1 is currently live. I would want to release V2 to a MIG without any reduction in capacity. Which of these options would you recommend to be set to 0?

- --max-surge  
    
- --max-unavailable - o
    
- --max-num-replicas 

Question 2:

True or False: Unmanaged instance group provides you with self-healing and auto-scaling capabilities

- True
    
- False - o

Question 3:

Can a MIG contain VMs created with different machine types?

- Yes
    
- No - o

Question 4:

How can you prevent frequent scaling up and down of VM instances in a MIG?

- --health-check
    
- --cool-down-period - o

Cloud Load Balancing
- Distributes user traffic across instances of an application in single region or multiple regions
	- Fully distributed, software defined managed service
	-  Important features: 
		- Health check - Route to healthy instances
			- Recover from failures
		- Auto Scaling
		- Global load balancing with single anycast IP
			- Also supports internal load balancing
- Enables:
	- High availability
	- Auto scaling
	- Resiliency

HTTP vs HTTPs vs TCP vs TLS  vs UDP
- Computers use protocols to communicate
- Multiple layers and multiple protcols
- Network layer - transfer bits and bytes
- Transport layer - Are the bits and bytes transferred properly
- Application layer - Make the rest API calls and send emails
- Each layer makes use of the layers beneath it
- Network layer:
	- IP (Internet Protocol): Transfer bytes, unreliable.
- Transport Layer:
	- TCP (Transmission Control): Reliability > Performance
	- TLS (Transport Layer Security): Secure TCP
	- UDP (User Datagram Protocol): Performance > Reliability
- Application Layer:
	- HTTP (Hyper text transfer protocol): Stateless Request Response Cycl
	- HTTPS: Secure HTTP
	- SMTP: Email Transfer Protocol
- Most applications typically communicate at application layer
	- Web apps/ REST API (HTTP/ HTTPS), Email servers (SMTP), File transfers (FTP)
	- All these applications use TCP/TLS at network layer (for reliability)
- However applications needing high performance directly communicate at transport layer:
	- Gaming applications and live video streaming use UDP (sacrifice reliabiltiy for performance)

Cloud Load Balancing - Terminology
- Backend - Group of endpoints that receive traffic from a google cloud load balancer (i.e instance groups)
- Frontend - Specify an IP address, port and protocol. This IP address is the frontend IP for your clients request
- Host and path rules (For HTTP(s) Loading Balancing) - Define rules redirecting the traffic to different backends: 
	- Based on path, host, or HTTP headers

Loading Balancing - SSL/TLS Termination/Offloading
- Client to Load Balancer: Over internet
	- HTTPS recommended
- Load Balancer to VM Instance: Through google network
	- HTTP is ok. HTTPS is preferred
- SSL/TLS Termination / Offloading
	- Client to Load Balancer: HTTPS/TLS
	- Load Balancer to VM instance: HTTP/TCP

Load Balance Across MIGs in Multiple Regions
- Regional MIG can distribute instances in different zones of a single region
	- Create multiple Regional MIGs in different regions (in the same project)
- HTTP(s) Load Balancing can distribute load to the multiple MIGs behind a single external IP address
	- User requests are redirected to the nearest region (low latency)
- Load balancing sends traffic to healthy instaces:
	- If health check fails instances are restarted:
		- Remember - Ensure that health can check from load balancer can reach the instance in an instance group
	- If all backends within a region are unhealthy, traffic is distributed to healthy backends in other regions

Quick Review of HTTP(S Load Balancing Concepts
-  Backend Service - Group of backends or ab ucket
- Backend - A managed Instance Group, for example
- URL Maps - Route request to backend services or backend buckets
	- URL /service-a maps to Backend Service A
	- URL /service-b maps to Backend Service B

Question 1:

True or False: HTTPS Load Balancing can load balance between MIGs in different regions

- True - o
    
- False

Question 2:

Which of these networking tiers is recommended if you want to use Global HTTPS Load Balancing?

- Premium Network Tier - o
    
- Standard Network Tier
  
Question 3:

How many HTTPS Load Balancing Backends would you need to support one version each of three different microservices, each with two MIGs in two different regions?

- 1 (One backend service can route between multiple microservices)
    
- 3 (One for each version of microservice)
    
- 6 (One for each MIG) - o