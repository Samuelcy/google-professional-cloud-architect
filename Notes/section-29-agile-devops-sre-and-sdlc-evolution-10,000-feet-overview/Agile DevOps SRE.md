Waterfall
- Requirements, Design, Implementation, Testing, Deployment

Spiral
- Vision, Iteration 1, Iteration 2..., Final Product

Agile
- Plan, Code, Build, Test, Release, Deploy, Review, Plan

DevOps
- Getting better at Three Elements of Great Software Teams
  - Communication - Get teams together
  - Feedback - Earlier you find a problem, easier is to fix
  - Automation - Automate testing, infrastructure provisioning, deployment, monitoring

DevOps - CI, CD
- Continuous Integration
	- Continuously run your tests and packaging
- Continuous Deployment
	- Continuous deploy to test environments
- Tools
	- Cloud Source Repositories: Fully-featured, private git repository
	- Container Registry: Store your Docker Images
	- Jenkins: Continuous integration
	- Cloud Build: Build deployable artifacts
	- Spinnaker: Multi-cloud continuous delivery platform
		- Release software changes with high velocity and confidence
- Infrastructure as Code

Google Cloud Deployment Manager
- All configured in YAML
- Templates: Reusable resource definitions that can be used in multiple configuration files
- Deployment: Collection of resources that are deployed and managed together
- Manifests: Read-only object containing original deployment configuration

Cloud Marketplace
- Cloud Marketplace: Central repo of easily deployable apps & datasets

Site Reliability Engineering (SRE)
- DevOps++ at Google
- SRE teams focus on every aspect of an application
	- Availability, latency, performance, efficiency, change management, monitoring, emergency response, and capacity planning
- Key Principles:
	- Manage by Service Level Objective (SLOs)
	- Minimize Toil
	- Move Fast by Reducing Cost of Failure
	- Share Ownership with Developers

Site Reliability Engineering (SRE) - Key Metrics
- Service Level Indicator (SLI): Quantitative measure of an aspect of a service
	- Availability, latency, throughput, durability, correctness
- Service Level Object (SLO): SLI + target
	- 99.99% Availability
- Service Level Agreement (SLA): SLO + Consequences (contract)
- Best Practices
	- Handling Excess Loads
		- Load Shedding
			- API Limits
			- Streaming Data
		- Reduced Quality of Service
	- Avoid Cascading Failures
		- Plan to avoid thrashing
			- Circuit breaker
	- Penetration Testing (Ethical Hacking)
		- Simulate an attack with the objective of finding security vulnerabilities 
	- Load Testing
		- Simulate real world traffic as closely as possible
	- Resilience Testing - "How does an application behaves under stress"
	- Resilience - "Ability of system to provide acceptable behavior even when one or more parts of the system fail"\
	- Approaches:
		- Chaos Testing (simian army) - Cause one or more layers to fail
Question 1:

Which of these is a multi-cloud continuous delivery platform that supports deployments to Google Compute Engine, Google Kubernetes Engine, Google App Engine, and other cloud platforms?

- Cloud Source Repositories
    
- Cloud Build
    
- Spinnaker -o 

Which of these is an open-source solution to provision infrastructure using Infrastructure as Code?

- Terraform - o
    
- Cloud Build
    
- Google Cloud Deployment Manager

Question 3:

Which of these tools can you use to perform Configuration Management (Install right software and tools on the provisioned resources) on Google Cloud?

- Terraform or Google Cloud Deployment Manager
    
- Ansible or SaltStack - o 

Question 4:

Which of these metrics is used to manage development velocity in SRE?

- Service Level Indicator(SLI)
    
- Service Level Objective (SLO)
    
- Error budgets - o 

Question 5:

Which of these is a recommended option to Handling Excess Loads?

- Load Shedding
    
- Reduced Quality of Service
    
- Both -o 

Question 6:

Which of these are the best practices with Load Testing?

- Simulate real world traffic as closely as possible
    
- Test for spiky traffic - suddenly increases in traffic
    
- Both  -o 

Question 7:

Which of these tools will make use of during Resilience Testing?

- Selenium to perform Automation Testing
    
- JUnit to perform Unit Testing
    
- Simian Army to perform Chaos Testing -o 

Question 8:

You are running a microservices architecture on GKE. As part of your testing, you terminated a node to see how the system reacts to it. What kind of testing are you performing?

- Resilience Testing - o
    
- Load Testing
