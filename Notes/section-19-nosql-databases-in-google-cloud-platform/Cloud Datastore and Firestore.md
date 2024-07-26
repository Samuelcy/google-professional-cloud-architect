Cloud Datastore and Firestore
- Datastore - Highly scalable NoSQL Document Database
	- Automatically scales and partitions data as its grows
		- For bigger volumes, BigTable si recommended
	- Supports Transactions, Indexes and SQL like queries (GQL)
		- Does not support Joins or Aggregate (sum or count) operations
	- For use cases needing flexible schema with transactions
		- Examples: Users Profile and Product Catalogs
	- Structure: Kind > Entity (Use namespaces to group entities)
	- You can export data ONLY from gcloud (NOT from cloud console)
		- Export contains a metadata file and a folder with the data
- Firestore = Datastore+++: Optimized for multi device access
	- Offline mode and data synchronization across multiple devices - mobile, IOT etc
	- Provides client side libraries - Web, iOS, Android and more
	- Offers Datastore and Native modes

Understanding Cloud DataStore Best Practices
- Cloud Datastore is a doucment store with flexible schema
	- Recommended for storing things like user profiles
	- Another use Case: Index for objects stored in Cloud Storage
		- You want to allow users to upload their profile pictures:
			- Store objects (pictures) in Cloud Storage
			- Enable quick search by storing metadata (like ids and cloud storage bucket, object details) in Cloud Datastore
- Design your keys and indexes carefully:
	- Avoid monotonically increasing values as keys
		- Not recommended - 1,2,3,.. Customer 1, Cust.. 2 , Cust .. 3
	- Created indexes only if they would be used in queries
		- For ad hoc queries on large datasets without pre-defined indexes, BigQuery is recommended
- Prefer batch operations (to single read, write or delete operations):
	- More efficient as multiple operations are performed with same overheard as one operation

Cloud BigTable
- Petabyte scale, wide column NoSQL DB (HBase API compatible)
	- Designed for huge volumes of analytical and operational data
		- IOT Streams, analytics, Time Series Data etc
	- Handle millions of read/write TPS at very low latency
	- Single row transactions (multi row transactions NOT supported)
- Not serverless: You need to create a server instance (Use SSD or HDD)
	- Scale horizontally with multiple nodes (No downtime for cluster resizing)
- Cannot export data using cloud console or glcoud:
	- Either use a Java application or HBase commands
- Use cbt command line tool to work with Big Table (NOT gcloud)
![[Pasted image 20240725154914.png]]

Designing BigTable Tables
- Cloud Bigtable is a key/value store
	- Each table has only one index, the row key
	- Design your row key based on your frequently used queries

Understanding Cloud BigTable Best Practice
- Recommended for streaming IOT & time series data
- Automatically shards data into multiple tablets across nodes in cluster:
- Cloud Bigtable supports SSD or HDD storage
	- SSD - For most usecases
	- HDD - For large non latency-sensitive data sets of size > 10 TB with very very few reads
- You can create a cloud bigtable instance with more than one cluster to enable replication (Cross Region or Cross Zone):
	- Independent copy of data is stored in each cluster (in the zone of the cluster)
	- Bigtable automatically replicates changes
	- Replication improves durability and availability of your data
		- Stores separate copies in multiple zones or regions
		- Can automatically failover between clusters if needed
	- Replication helps you to put data closer to your customers
		- Configure an application profile or app profile with routing policy of multi-cluster roouting
			- Automatically route nearest cluster in an instance

Question 1:

Which of these a document data store that can be used to store things like user profiles?

- Cloud Datastore - o
    
- Cloud SQL

Question 2:

Which of these NoSQL databases allow you to create multiple indexes on a table?

- Cloud Datastore - o
    
- Cloud Bigtable 

Question 3:

Which of these NoSQL databases allow you to store huge volumes of analytical and operational data?

- Cloud Datastore
    
- Cloud Bigtable - o

Question 4:

Which of these options can you use to increase the availability of Cloud Bigtable and decrease latency to end-users?

- Add a cluster to the Cloud Bigtable instance in a new region or new zone - o
    
- Create a new Cloud Bigtable instance