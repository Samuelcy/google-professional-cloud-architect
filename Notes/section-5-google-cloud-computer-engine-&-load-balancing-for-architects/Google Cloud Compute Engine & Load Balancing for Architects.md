Compute Engine & Load Balancing for Architects

Professional Cloud Architect vs Associate Cloud Engineer
- Engineer
	- Focused on tasks that Cloud Engineers perform in day to day job
- Architect
	- Understand business and technical requirements
	- Design cloud solutiosn taht meet your functional and non-functional needs
-  GCP Services are the same
	- Perspective should be different

Availability

High Availability for Compute Enginer & Load Balancing
- Highly available architecture
	- Multiple regional instance groups for each microserve
	- Distribute load using a Global HTTPS Load Balancing
	- Configure Health Checks for Instance Group and Load Balancing
	- Enable Live Migration for VM instances
- Advantages
	- Instances distributed across regions
		- Even if a region is down, your app is available
	- Global Load balance is highly available
	- Health hecks ensure auto healing

What is Scalability
- A system is handling 1000 transactions per second. Load is expected to increase 10 times in the next month
	- Can we handle a growth in users, traffic, or data size?
	- Does ability to serve more growth increase proportionally with resources?
- Ability to adapt to changes in demand (users,data)

What is vertical scaling?
- Deplying application / database to bigger instance:
	- Larger hard drive
	- Faster CPU
	- More Ram, CPU, I/O, networking capabilities

Horizontal Scaling
- Deplying multiple instances of applicaiton / database
- Horizontal scaling is preferred to Vertical Scaling
	- Vertical scaling has limits
	- Vertical scaling can be expensive
	- Horizontal scaling increases availability
	- Horizontal scaling needs additional infrastructure: Load balancers etc.

Compute Engine: Live Migration & Availability Policy
- Live Migration
	- Your instance is migrated to another host in the same zone
	- Does NOT change any attributes or properties of the VM
	- Supported for instances with local SSDs
	- Not supported for GPUs and preemptible instances
- Important Configuration - Availability Policy:
	- On host maintenance: 
		- Migrate (default): Migrate VM instance to other hardware
		- Termiante: Stop the VM instance
	- Automatic restart - Restart VM instance if they are terminated due to non-user-initiated reasons(maintenances, failure) 

Compute Engine Features: GPUs
- Adding a GPU to your VM
	- High perforamnce for math intensive and graphics intensive workloads
	- Higher cost
	- Use images with GPU libraries (deep learnign) isstalled
	- GPU restrictions
		- Not support on all machine types
		- On host maintenace can only have the value "Terminate VM Instance"
	- Recommended Availability policy for GPUs
		- Automatic restart - on

Compute Engine & Load Balancing for Architects
- Security
	- Use Firewall Rules to restrict traffic
	- Use internal IP addresses as much as possible
	- Use sole-tenant nodes when you have regulatory needs
	- Create a hardened custom image to launch your VMs
- Performance
	- Choose right Machine Family for your workload
	- Use GPUs and TPUs to increase perforamnce
		- Use GPUs to accelerate machine learning and data processing workloads
		- Use TPUs for massive matrix operations performancedi n your machine learning workloads

Resiliency for Compute Engine and Load Balancing
- Resiliency - "Ability of system to provide acceptable behavior even when one or more parts of the system fail"

Sustained use discounts
- Automatic discounts for running VM instances for significant portion of the billing month
- Applicable for instances created by Google Kubernetes Engine and Compute Engine
- Restriciton: Does not apply on certain machine types
- Restriction: Does not apply to VMs created by App Enginer flexible and Dataflow

Committed use discounts
- For workloads with predictable resource needs
- Commit for 1 year or 3 years
- Up to 70% discount based on machien type and GPUs

Preemptible VM
- Short-lived cheaper (up to 80%) compute instances
	- Can be stopped by GCP any time (preempted) within 24 hours
	- Instances get 30 second warning 9to save anythign they want to save)
- Use preempt VM's if
	- Your applications are fault tolerant
	- You are very cost sensitive
	- Your workload is not immediate
- Restrictions
	- Not always available, cannot be migrated to VMs, no automatic restart

Spot VMs
- Spot VMs: Latest version of preemptible VMs
- Key difference: does not have a maximum runtime, compared to traidtional preempt VMs with a max time for 24 hours

Google Compute Engine - Billing
- You are billed by the second (after 1 min)
- You are not billed for compute when a compute instance is stopped
	- However, you will be billed for any

Compute Engine & Load Balancing - Cost Efficiency
- Use auto scaling
	- Have optimal number and type of VM instances running
- Understand sustained use discounts
- Make use of committed use discounts for predictable long term workloads
- Use preemptible VMs for non critical fault tolerant worklloads
- 

Question 1:

You want to keep your costs to a minimum. Which of these would you use for a non-time-critical fault-tolerant batch program?

- Committed use discounts
    
- Preemptible VM - o

Question 2:

What of these statements about Preemptible VM are TRUE?

- Can be stopped by GCP anytime within 24 hours
    
- Instances get a 30 second warning to react
    
- Preemptible VMs are the cheapest VM options
    
- All of the above - o 
  
Question 3:

Which of these is recommended for a web application that runs continuously serving hundreds of thousands of users?

- Committed use discounts - o
    
- Preemptible VM

Question 4:

Enabling Live Migration on a VM instance helps you with increasing:

- Resiliency
    
- Availability
    
- Both - o
    
- None
  
True or False: Vertical Scaling increases the availability

- True
    
- False - o