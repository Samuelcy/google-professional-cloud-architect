Cloud Migration Planning
- Phase 1: Asses the workloads to be migrated
- Phase 2; Plan the foundation
- Phase 3: Deploy the workloads
- Phase 4: Optimize your environment

Cloud Migration Approaches
- You have a combination of following options:
	- Rehosting ("Lift and shift")
	- Replatforming
		- Few adjustments to suit the cloud
		- Example: Containerizing
	- Repurchasing
		- Move to a new, cloud-native produc
			- Move to a new databse
	- Refactoring
		- Example: Serverless computing
		- Most expensive
	- Retiring
		- End of service
	- Retaining
		- Do NOT move to cloud
		- Stay on promises


Cloud Migration Planning - Phases 1 & 2
- Phase 1: Asses the workloads to be migrated
	- Take inventory and catalog apps
	- Experiment and design proofs of concept
	- Calculate total cost of ownership
	- Choose which workloads to migrate first
		- Base on business value, teams, dependencies, refactoring effort, licensing, and compliance needs
- Phase 2: Plan the foundation
	- Design Resource Organization Hierarchy, Configure IAM (users, groups, integrate with Identity Provider (idP)) and Design network topology and connectivity
	- Plan for security (data, apps), Monitoring (and alerting) and Governance
	- Plan your migration Team
- Phase 3: Deploy the workloads
	- Migrate data
		- Consider, Time, Offline versus online transfer options and security
	- Deploy Applications
- Phase 4: Optimize your environment
	- Ensure that logging, monitoring and alerting are in place
	- Reduce overhead by preferring managed services
	- Optimize costs using autoscaling
