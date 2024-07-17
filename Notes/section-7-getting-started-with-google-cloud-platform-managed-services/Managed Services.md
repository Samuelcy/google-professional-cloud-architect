IAAS (Infrastructure from cloud provider)
- Example: Using VM to deploy your applications or databases

PAAS (Platform as a Service)
- Cloud provider is responsible for
	- OS (inc. updates and patches)
	- Application Runtime
	- Auto scaling, availability and load balancing
- You are responsible for
	- Configuration (of application and services)
	- Application code (if needed)
- Varieties:
	- CAAS (container as a service): Containers instead of Apps
	- FAAS (Function as a service): Functions instead of Apps

Microservices
- Enterprises are heading towards microservices architectures
	- Build small focused microservices
	- Flexibility to innovate and build applications in different programming languages 
- But deployments become complex

Containers - Dockets
- Create docker images for each microservice
- Docker image has all needs of a microservice
	- Application runtime (JDK or python or nodejs)
	- Application code and dependencies
- Runs the same way on any infrastructure
	- Your local machine
	- Corporate data center
	- Cloud
- Advantages
	- Docker containers are light weight
		- Compared to virtual machines as they do not have a Guest OS
	- Docker provides isolation for containers
	- Docker is a cloud neutral

Container Orchestration
- Auto scaling - scale containers based on demand
- Service discovery - help microservices find one another
- load balancer - distribute load among multiple instances of a microservice
- self healing - do health checks and replace failing instances
- Zero downtime deployments - release new versions without downtime

Serverless
- Don't worry about infrastructure


Question 1:

You want to migrate a custom C++ application running on a customized Linux VM as-is to Google Cloud. Which of these services would you recommend?

- Compute Engine - o
    
- App Engine Standard
    
- Cloud Functions
Which of these is the managed container orchestration service in Google Cloud?

- Google Kubernetes Engine - o
    
- Compute Engine
    
- App Engine
    
- Cloud Functions

Question 3:

Which of these can be used to build event-driven applications using simple, single-purpose functions in Google Cloud?

- Compute Engine
    
- Google Kubernetes Engine
    
- App Engine
    
- Cloud Functions - o
  
  
Question 4:

Which of these Google Cloud services is used to create high-performance and general-purpose VMs that scale globally?

- Compute Engine - o
    
- Google Kubernetes Engine
    
- App Engine
    
- Cloud Functions