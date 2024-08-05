BigQuery - datawarehouse
- Exabyte scale modern Datawarehousing solution from GCP
	- Relational database (SQL, schema, consistency etc)
		- Use SQL-like commands to query massive datasets
	- Traditional (Storage + Compute) + Modern (Realtime + Serverless)
- When we are talking about a Datawarehouse, importing and exporting data (and formats) becomes very important:
	- Load data from a variety of sources, incl. streaming data
	- Export to Cloud Storage (long term storage) & Data Studio (visualization)
- Automatically expire data (Configurable Table Expiration)
- Query external data sources without storing data in BigQuery
	- Cloud storage cloud sql, BigTable, Google Drive
	- Use permanent or temporary external tables

Accessing and Querying Data
- Access databases using:
	- Cloud console
	- bq command-line tool (NOT gcloud)
	- BigQUery Rest API OR
	- HBase API based libraries (Java, .Net & Python)
- (Remember) BigQuery queries can be expensive as you are running them on large data sets!
- (Best Practice) Estimate Bigquery queries before running

Paritioning and Clustering BigQuery Tables - Usecase
- You pay for BigQuery queries by the amount of data scanned
- How do you reduce your costs of querying BigQuery and improve performance?
- Scenario: Imagine a questions

Paritioning and Clustering BigQuery Tables
- Partitioning: Table is divided into segments
	- Makes it easy to manage and query your data
	- Improves performance and reduce costs
	- Partition based on Ingestion time (arrival time) OR a column (TIMESTAMP, DATA, or DATETIME, or INTEGER)
	- Allow partitions will share same schema as table
	- Allows you to expire (delete) parts of table data data easily
- Clustering: Organize table data based on the contents of one or more columns
	- Goal: alocate related data and eliminate scans of unnecessary data
	- Avoid creating too many small partitions (of less than 1GB). In those cases, prefer Clustering

Expiring Data in BigQuery
- BigQuery Hierarchy: Data Set > Table > Paritions
	- Configure expiration at each level

Importing Data into BigQuery
- Batch Import (FREE)
	- Import from Cloud Storage and local files
	- Import after processing by Cloud Dataflow and Cloud Dataproc
- Streaming Import ($)
	- From Cloud Pub/Sub, streaming inserts
	- Import after processing by Cloud Dataflow and Cloud Dataproc
- Federated Queries: Query external data
	- Cloud Storage, Cloud SQL, BigTable, Google Drivfe
- BigQuery Data Transfer Service: Import from 
	- Google SaaS apps (Google Ads, Cloud Storage etc)
	- External cloud storage providers - Amazon S3
	- Data warehouses - Teradata. Amazon Redshift

Streaming Data into BigQuery
- Loading data in bulk is free but streaming data is not FREE
- Streaming data can contain duplicates. How can you avoid it?
	- Add insertId with each streaming insert:
		- InsertId is used to provide best effort de-duplication (for up to one minute)
- There are strict streaming quotas with BigQuery:
	- If you are not populating insertId:
	- Else you are using insertId

Understanding BigQuery Best Practices
- Estimate your queries before running them
- Use clustering and partitioning for yoru tables
- Avoid streaming inserts when possible
	- Loading data in bulk is free but streaming data is NOT FREE
	- Offers Best effort de-duplication (when you use insertId)
	- Remember Quota limits
- Expire Data Automatically
	- Configure data default table expiration
	- Configure expiration time for tables
	- Configure partition expiration for paritionined tables
- Consider Long-term storage option
	- Long-term stoarge: Table in which data is NOT edited for 90 consecutive days
	- Lower Storage cost - Similar to Cloud Storage Nearline
- BigQuery is fast for complex queries:
	- BUT it is not as well optimized for narrow -  range queries (Prefer Cloud BigTable)
- Optimize Big Query usage using audit logs
	- Analyze queries / josb that were run earlier
	- Stream your audit logs (BigQueryAuditMetaData) to BigQuery

Cloud Dataproc
- Managed Spark and Hadoop Service:
	- Variety of jobs are supported
	- Perform complex batch processing
- Multiple Cluster Modes:
	- Single Node / Standard / High Availability
	- Use regular / preemptible VMs
- Use case: Move your Hadoop and Spark clusters to the cloud
	- Perform your machine learning and AI development using open source frameworks
- (Remember) Cloud Dataproc is a data analysis platform
	- You can export cluster configuration but NOT data
- (Alternative) BigQuery - When you run SQL queries on Petabytes
	- Go for Cloud Dataproc when you need more than queries (Example: Complex batch processing Machine Learning and AI workloads)
Question 1:

Which of these options can you consider to reduce the costs of your BigQuery jobs?

- Partitioning
    
- Clustering
    
- Configure Table and Partition Expiration
    
- All of the above - o

Question 2:

Which of these helps you divide a table into multiple segments based on the ingestion date?

- Partitioning - o
    
- Clustering

Question 3:

How can you co-locate related data in a BigQuery table and eliminate scans of unnecessary data?

- Partitioning
    
- Clustering - o



Question 4:

Which of these options would you recommend to import data from Amazon S3, Amazon Redshift, or an on-premise Teradata installation into BigQuery?

- Streaming Import
    
- Federated Queries
    
- BigQuery Data Transfer Service - o

Question 5:

You are running complex Machine Learning and AI workloads on your Hadoop and Spark clusters. You want to move these workloads to Google Cloud. Which of these services would you recommend?

- Cloud BigQuery
    
- Cloud Dataproc - o