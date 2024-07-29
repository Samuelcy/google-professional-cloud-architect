Cloud Monitoring
- Monitor infrastructure
- Measure key aspects of services (Metrics)
- Create visualizations (Graphs and Dashboard)
- Configure Alerts (when metrics are NOT healthy)

Cloud Monitoring - Workspace
- Workspaces are needed to organize monitoring information

Cloud Monitoring - Virtual Machines
- Default metrics monitored include:
	- CPU utilization
	- Some disk traffic metrics
	- Network traffic,
	- Uptime Information
- Install Cloud Monitoring agent on the VM to get more disk, CPU, network, and process metrics:
	- Collectd - base daemon
	- Gathers metrics from VM and sends them to Cloud Monitoring

Cloud Logging
- Real time log management and analysis tool
- Allows to store, search, analyze and alert on massive volume of data
- Exabyte scale, fully managed service
	- No server provisioning, patching etc
- Ingest Log data from any source
- Key Features:
	- Logs Explorer - Search, sort & analyze using flexible queries
	- Logs Dashboard - Rich visualization
	- Logs Metrics - Capture metrics from logs (using queries / matching strings)
	- Logs Router - Route different log entries to different destinations

Cloud Logging - Audit and Security Logs
- Access Transparency Log: Captures Actions performed by GCP team on your content (NOT supported by all services):
	- Only for organizations with Gold support level & above
- Cloud Audit Logs: Answers who did what, when and where:
	- Admin activity logs
	- Data access logs
	- System event audit logs
	- Policy denied audit logs
![[Pasted image 20240728194314.png]]
Cloud Logging
- Required: holds admin activity, system events and access transparency logs (retained for 400 days)
	- 0 charged
	- You cannot delete the bucket
	- You cannot change retention period
- Default: All other logs (retained for 30 days)
	- You are billed based on Cloud Logging pricing
	- You cannot delete the bucket:
		- But you can disable the default log sink route to disable ingestion

Cloud Logging - Export
- Logs are ideally stored in CLoud logging for limited period

Cloud Logging - Use cases
- Use Case 1: trouble shoot using VM logs:
	- Install cloud logging agent in all VMs and sends logs to cloud logging
	- Search for logs in cloud logging
- Use Case 2: Export VM logs to BigQuery for querying using SQL like queries:
	- Install cloud logging agent in all VM's and send logs to Cloud Logging
	- Create a BigQuery dataset for storing the logs
	- Create an export sink in Cloud Logging with BigQuery dataset as sink destination
- Use Case 3: You want to retain audit logs for external auditors at minimum cost
	- Create an export sink in Cloud Logging with Cloud Storage bucket as sink destination
	- Provide auditors with Storage Object Viewer role on the bucket
	- You can use Google Data Studio also (for visualization)

Cloud Trace
- Distrbuted tracing systm for GCP: Collected latency data from:
	- Supported Google CLoud Services
	- Instrumental applications (using tracing libraries) using CLodu Trace API

Cloud Debugger
- Cloud Debugger: Capture state of a running application
	- Inspect the state of the application directly in the GCP encironment
	- Take snapshots of variables and call stack
	- No need to add logging statements
	- No need to redeploy
	- Very lightweight => very light impact to users

Cloud Profiler
- Cloud Profiler - Statistical, low-overhead profiler
	- Continously gather CPU and memory usage from production systems
	- Connect profiling data with application source code
		- Easily identify performance bottle necks
	- Two major components:
		- Profiling agent (collects profiling information)
		- Profiler interface (visualization)

![[Pasted image 20240728201940.png]]
Question 1:

Which of these is recommended service to trace calls across microservices in GCP?

- Cloud Debugger
    
- Cloud Trace - o
    
- Cloud Monitoring

Question 2:

Which of these services can be used to debug issues directly in production environments?

- Cloud Debugger - o
    
- Cloud Trace
    
- Cloud Monitoring

Question 3:

Which of these is NOT a type of Cloud Audit Logs?

- Admin activity Logs
    
- Access Transparency Log - o
    
- Data Access Audit Logs
    
- Policy Denied Audit Logs

Question 4:

Which of these destinations can be used as sinks for exporting log data from Cloud Logging?

- Cloud Storage
    
- Cloud BigQuery
    
- Cloud Pub/Sub
    
- All of the above - o