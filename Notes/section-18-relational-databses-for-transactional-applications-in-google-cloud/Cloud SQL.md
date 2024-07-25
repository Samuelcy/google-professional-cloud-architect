Cloud SQL
- Fully Managed Relational Database service
	- Configure your needs and do NOT worry about managing the database
	- Supports MySQL, PostgreSQL, and SQL Server
	- Regional Service providing High Availability (99.95%)
	- Use SSDs or HDDs (For best performance: use SSDs)
	- Up to 416 GB of RAM and 30 TB of data storage
- Use Cloud SQL for simple relational use case:
	- To migrate local MySQL, PostgreSQL, and SQL Server databases
	- To reduce your maintenance cost for a simple relational database
	- (REMEMBER) Use Cloud Spanner (Expensive) instead of Cloud SQL if:
		- You have huge volumes of relational data (TBs) OR
		- You need infinite scaling for a growing application (to TBs) OR
		- You need a Global (distributed across multiple regions) DATA OR
		- You need higher availability (99.999%)

SQL Commands
1. # Cloud SQL
2. gcloud sql connect my-first-cloud-sql-instance --user=root --quiet
3. gcloud config set project glowing-furnace-304608
4. gcloud sql connect my-first-cloud-sql-instance --user=root --quiet
5. use todos
6. create table user (id integer, username varchar(30) );
7. describe user;
8. insert into user values (1, 'Ranga');
9. select * from user;

Cloud SQL - Features
- Important Cloud SQL  Features
	- Automatic encryption (tables/backups), maintenance and updates
	- High availability and failover:
		- Create a standby with automatic failover
		- Pre requisites: Automated backups and Binary Logging
	- Read replicas for read workloads:
		- Options: Cross-zone, cross-region, and External (NON Cloud SQL DB)
		- Pre requisites: Automated backups and Binary logging
	- Automatic storage increase without downtime (for newer versions)
	- Point-in-time recovery: Enable binary logging
	- Backups (Automated and on-demanded backups)
	- Supports migration from other sources
		- Use Database Migration Service (DMS)
	- You can export data from UI (console) or gcloud with formats:
		- SQL (Recommended if you improt data into other databases and CSV)

Cloud SQL - High Availability
- Create a High Availability (HA) configuration
	- Choose Primary and Secondary zones within a region
	- You will have two instances: Primary and Secondary instances
- Changes from primary are replicated synchronously to secondary
- Changes from primary are replicated synchronously to secondary
- In case of Zonal failure, automatic failover to secondary instance:
	- If Primary zone becomes available, failover does not revert automatically
- High Availability setup CANNOT be used as a Read Replica

Understanding Cloud SQL Best Practices
- Use Cloud SQL Proxy:
	- Securely connect to Cloud SQL from your apps (GAE, Cloud Functions, Cloud Run, GKE etc)
- Understand Scalability
	- Enable HA configuration for high availability
		- Primary instance and a standby instance created in the same Region (Remember - Regional)
	- Read replicas help you offload read workloads
		- Remember Read replicas do not increase availability

Understanding Cloud SQL Best Practices -2
- Understand Backup and Export options"
	- Backups are lightweight and provide point in time recovery
		- But Backups are deleted when an instance is deleted
		- And you can't back up a single database or table
	- Exports take longer but they provide you with more flexibility
		- You can export a single database or table
		- (Remember) Exporting large databases can impacts the performance of a Cloud SQL database
			- Use serverless export (flag-offload) to reduce impact
				- Cloud SQL creates a separate, temporary instance to offload the export operation
		- Import / Export in multiple small batches instead of large batches

Cloud Spanner
- Fully managed, mission critical, relational (SQL), globally distributed database with very high availability (99.999%) 
	- Strong transactional consistency at global scale
	- Scales to PBs of data with automatic sharing
- Cloud Spanner scales horizontally for reads and writes
	- Configure no of nodes
	- (REMEMBER) In comparison,  Cloud SQL provides read replicas:
		- But you cannot horizontal scale write operations with Cloud SQL!
- Regional and Multi-Regional configurations
- Expensive (compared to Cloud SQL): Pay for nodes & storages
- Data Export: Use Cloud Console to export data
	- Other option is to use Data flow to automate export
	- no gcloud export option

Cloud Spanner - Table Creation Script

1. CREATE TABLE Users (
2.   UserId   INT64 NOT NULL,
3.   UserName  STRING(1024)
4. ) PRIMARY KEY(UserId);


Question 1:

Which of these would you use when you need a Relational Database for a Global transactional application?

- Cloud SQL
    
- Cloud Spanner - o

Question 2:

Which of these can you use to increase the availability of your Cloud SQL instance?

- Create HA Configuration - o
    
- Create a Read Replica

Question 3:

Which of these can you use to increase the scalability of your Cloud SQL instance by offloading read workloads?

- Create HA Configuration
    
- Create a Read Replica - o