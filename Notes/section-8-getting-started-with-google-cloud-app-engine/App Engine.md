App Engine
- Simplest way to deploy and scale your applications in GCP
	- Provides to end to end application management
- Support
	- Go, Java, .Net,, Python, Ruby use pre-configured runtimes
	- Use custom run-time and write code in any language
	- Connect to variety of google clodu stoarge products
- No usage charges - Pay for resources provisioned
- Features
	- Automatic load balancing and auto scaling
	- Managed platform updates & application health monitoring
	- Application versioning
	- Traffic splitting

Compute Engine vs App Enginee
- Compute Engine
	- IAAS
		- More flexibility
		- More responsibility
			- Choose image
			- Installing software
			- Choosing hard
			- ware
			- Fine grained Access / Permission (Certificates / Firewalls)
			- Availability etc
- App Engine
	- PaaS
	- Serverless
	- Lesser Responsibility
	- Lower Flexibility

App Engine Environments
- Standard: Applications run in langauge specific sandboxes
	- Complete isolation from OS/Disk/Other Apps
	- V1: Java, Python, PHP, Go (Old Versions)
		- Only for python and php runetimes
			- restricted netwrok access
			- only white listed extensions and libraries are allowed
	- V2: Java, Python, PHP, Node.js, Ruby, Go (Newer Versions)
		- Full network access and no restrictions on language extensions
- Flexible - Application instances run within Docker containres
	- Make use of Compute Engine virtual machines
	- Support ANY run time (with built in support for Python, Java, Node.js, Go, Ruby, PHP, or .NET)
	- Provides access to background processes and local disk

App Engine - Application component hierarchy
- Application: One App per Project
- Service(s): Multiple Microservices or App components
	- You can have multiple services in a single application
	- Each service can have different settings
	- Earlier called Modules
- Version(s): Each version assocaited with code and configuration
	- Each version can run in on or more isntances
	- multiple versions can co-exist
	- Options to roll back and split traffic
![[Pasted image 20240717142124.png]]

App Engine - Scaling Instances
- Automatic - Automatically scale instances on the load:
	- Recommended for Continuously Running Workloads
		- Auto scale based on:
			- Target CPU utilization - Configure a CPU usage threshold
			- Target Throughout Utilization - Configure a throughput threshold
			- Max Concurrent Requests - Configure max concurrent requests an instance can receive
		- Configure Max Instances and Min Instances
- Basic - Instances are created as and when requests are received:
	- Recommended for Adhoc Workloads
		- Instances are shutdown if ZERO rqeuests
			- Tried to keep costs low
			- High latency is possible
		- Not supported by App Engine Flexible Environment
		- Configure Max Instances and Idle Timeout
- Manual - Configure specific number of instances to run
	- Adjust number of instances manually over time
	  

App Engine - From the Command Line

1. cd default-service
2. gcloud app deploy
3. gcloud app services list
4. gcloud app versions list
5. gcloud app instances list
6. gcloud app deploy --version=v2
7. gcloud app versions list
8. gcloud app browse
9. gcloud app browse --version 20210215t072907
10. gcloud app deploy --version=v3 --no-promote
11. gcloud app browse --version v3
12. gcloud app services set-traffic split=v3=.5,v2=.5
13. gcloud app services set-traffic splits=v3=.5,v2=.5
14. watch curl https://melodic-furnace-304906.uc.r.appspot.com/
15. gcloud app services set-traffic --splits=v3=.5,v2=.5 --split-by=random

17. cd ../my-first-service/
18. gcloud app deploy
19. gcloud app browse --service=my-first-service

21. gcloud app services list
22. gcloud app regions list