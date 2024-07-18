Key enhancements in 2nd Gen compared to 1st Gen
- Longest request time out: up to 60 minutes for http-triggered functions
- Larger instances: Up to 16GiB ram with 4 vCPU
- Concurrency: Up to 1000 concurrent requests per function instance
- Multiple function revisions and traffic splitting supported

Cloud Functions - Scaling and Concurrency
- Typical serverless functions architecture
	- Autoscaling - As new invocations come in, new function instances are created
	- One function instance handles ONLY ONE request AT A Time
	- 3 concurrent functions invocations => 3 function instances
		- If a 4th function invocation occurs while existing invocations are in progress, a new function instances will be created
		- However, a function instance that completed execution may be reused for future requests
	- Cold Start:
		- New function instance initialization from scratch can take time
		- (Solution) Configure Min number of instances (increases cost)
- 1st Gen uses the typical server less functions architecture
- 2nd Gen adds a very important new feature
	- One function instance can handle multi0ple requests AT THE SAME TIME
		- Concurrency: How many concurrent invocations can one function instance handle (Max 1000)

Cloud Functions - Best Practices
- To avoid cold starts, set min no of instances (increases cost)
	- Minimize dependencies (loading dependencies increases initialization time)
- Configure max no of instances (protect from abnormally high request levels)
- Use Cloud Endpoints (or Apigee or API gateway) for versioning
- Use Cloud Run (& Cloud functions gen 2) revisions for safer releases:
	- Configure which revisions should receive traffic and how much
	- You can rollback to a previous revision, if needed
- Use Secret Manager to securely store secrets
- Use Individual Service Accounts for each Function
	- Grant roles / cloudfunctions.invoker role to invoke a cloud function
- 