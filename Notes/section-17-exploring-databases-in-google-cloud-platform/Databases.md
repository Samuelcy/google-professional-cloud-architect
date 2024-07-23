Databases Primer
- Databases provide organized and persisten storage for your data
- To choose between different database types, we would need to understand:
	- Availability
	- Durability
	- RTO
	- RPO
	- Consistency
	- Transactions

Availability and Durability
- Availability
	- Percentage of tiem an applciation provides the operations expected of it
- Durability
	- How long will data persist?
- 4'9 = 99.99 = good

Increasing Availability and Durability of Databases
- Increase availability
	- Multiple standbys available or distribute the database
		- in multiple zones, regions
- Increase durability
	- Multiple copies of the data (standbys, snapshots, transaction logs and replicas)
		- in multiple zones, in multiple regions

RPO (Recovery Point Object): Maximum acceptable period of data loss
RTO (Recovery Time Objective): Maximum acceptable downtime

![[Pasted image 20240722182608.png]]

Consistency
- Strong consistency - Synchronous replication to all replicas
	- Will be slow if you have multiple replicas or standbys
- Eventual consistency - Asynchronous replication. A little lag - few seconds - before the change is available in all replicas
	- In the intermediate period, different replicas might return different values
	- Used when scalability is more important than data integrity
	- Examples: Social Media Posts - Facebook status messages, Twitter tweets, Linked in posts etc
- Read-after-Write consistency - Inserts are immediately available
	- However, updates would have eventual consistency

Database Categories

Relational Database - OLTP (Online Transction Processing)
- Applications where large number of users make large number of small transaction
- Use cases:
	- Most traditional applications, ERP, CRM, e-commerece, banking applications

Relational Database - OLAP (Online Analytics Processing)
- Applications allowing users to analyze petabytes of data
	- Examples: Reporting applications, Data ware houses, Business intelligence applications, Analytics systems
	- Sample application: Decide insurance premiums analyzing data from last hundred years
	- Data is consolidated from multiple (transactional) databases
- OLAP and OLTP use similar data structus but different approach in how data is stored
- OLTP databases use row storage
	- Each table row is stored together
	- Efficient for processing small transactions
- OLAP databases use columnar storage 
	- Each table column is stored together
	- High compression - Store petabytes of data efficiently
	- Distribute data - One table in multiple cluster nodes
	- Execute single query across multiple nodes - Complex queries can be executed efficiently

NoSQL Databases
- Flexible schema
	- Structure data the way your application eneds it
- Horizontally scale alot of data
- Not a 100% accurate generalization but a great starting point:
	- Typical NoSQL databases trade-off "Strong consistency and SQL features" to achieve "scalability and high-performance"
- Google Managed Services:
	- Cloud Firestore (Datastore)
	- Cloud BigTable

Cloud Firestore (Datastore) vs Cloud BigTable
- Cloud Datastore - Managed serverless NoSQL document database
	- Provides ACID transactions, SQL-like queries, indexes
		- Designed for transactional mobile and web applicaitons
	- Firestore (next version of Datastore) adds:
		- Strong consistenc
		- Mobile and Web client libraries
	- Recommended for small to medium databases (0 to a few Terabytes)
- Cloud BigTable - Managed, scalable NoSQL wide column database
	- NOT serverless (You need to create the instances)
	- Recommended for data size > 10 Terabytes to sveveral Petabytes
	- Recommended for large analytical and operational workloads
		- Not recommended for transactional workloads

In-memory Databases
- Retriveing data from memory is much faster than retriveing data from disk
- In-memory databases like Redis deliver microsecond latency by storing persistent data in memory
- Recommended GCP Managed Service
	- Memory Store
- Use cases: Caching, session management, gaming leader boards, geospatial applications

![[Pasted image 20240722185455.png]]

![[Pasted image 20240722185657.png]]Question 1:

RPO is a measure of

- Maximum acceptable period of data loss - o
    
- Maximum acceptable period of DB downtime
    
- Maximum acceptable period of High availability

Question 2:

Which of these is a Relational OLAP (Analytics) database service in GCP?

- Cloud SQL
    
- Cloud Datastore
    
- Cloud BigQuery - o 

Question 3:

Which Database service is a managed, NoSQL wide column database suitable for huge databases (> 10 TB)?

- Cloud Spanner
    
- Cloud BigQuery
    
- Cloud BigTable - o 
    
- Cloud DataStore

Question 4:

Which DB service is recommended for huge volumes (Petabytes) of streaming data from IOT devices?

- Cloud Spanner
    
- Cloud BigTable - o
    
- Cloud DataStore