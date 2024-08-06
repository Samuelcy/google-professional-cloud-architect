Caching
- How can reduce the load on 
	- Your data stores
	- Your serves
- Use Caching
	- Caching Usecases:
	- Caching infrequently chagnign data in Database
	- Caching user sessions from applications
	- Caching static content
	- Caching infrequently changing dynamic content

Memory Store
- In - memory datastore service: Reduce access times
- Fully managed (Provisioning, Replication, Failover & Patching)
	- Highly avilable with 99.9% SLA
	- Monitoring can be easily setup using Cloud Monitoring
- Support for Redis and Memcached:
	- Use Memcached for caching
		- Reference data, database query caching, session store etc
	- Use Redis for low latency access with persistence and high availability
		- Gaming leader boards etc
- Can be accessed from:
	- Compute Engine
	- App Engine flexible and standard
	- Google Kubernetes Engine
	- Cloud functions

App Engine memcache service
- Legacy in-memory data cache specifically for App Engine applications 
	- Example Use Cases:
		- Speed up common datastore queries
		- Caching session data and user preferences
	- Temporary storage (not backed by persistent storage)
	- Two Service levels:
		- Shared memcache (FREE)
		- Dedicated memcache ($): Fixed cache capacity dedicated to your app 
			- Predictable performance
			- Billed by the GB - hour of cache size 

Cloud CDN - Content Delivery Network
- Use Google's global edge network to serve global content with low latency
- Integrates with External HTTP(S) Load Balancing
	- LB provides frontend IP addresses and ports
- Backends can be:
	- Cloud Storage Buckets, Instance groups, App Engine, Cloud Run, or Cloud Functions
	- Endpoints outside of Google Cloud (custom origins)
- How cloud cdn works?
	- External HTTP(s) Load Balancing uses proxies - Google Front Ends (GFEs)
			- Request from user arrives at a Google Front END (GFE)
			- If URL maps to a backend with Cloud CDN configured:
				- If content is found in cache (Cache hit), GFE sends cached resposne
				- If content is NOT found in the cache (cache miss), request is forwarded to backend (origin server)
					- Response is sent to user and cached
				- Using TTL settings to control cache duration

Cloud CDN - Best Practices
- Cache static content
- Be careful with expiring time-sensitive (or dynamic) content
- Using custom cache keys to improve cache hit ratio