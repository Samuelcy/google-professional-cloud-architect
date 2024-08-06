Data Lifecycle
- Four steps:
	- Ingest: Stream or batch ingest
	- Store: Durably and cost efficiently store data in a convenient format
	- Process and analyze: Convert data to information (normalizations or aggregations)
	- Explore and visualize: Flexibility to play with data / information. Get and share insights

Data Lifecycle - 1 - Ingest
- Streaming: Pub / Sub
- Batch: Storage Transfer Service, BigQuery Transfer Service, Transfer APpliance, gsutil etc
- Database migration: Migrate data from other sources to Google Cloud
	- Database Migration Service (Simplifying migrations to cloud SQL)
	- Batch transfer to Cloud Storage
	- Load data into database from Cloud Storage using Dataflow

Data Lifecycle - 2 - Store
![[Pasted image 20240805143648.png]]

Data Lifecycle - 3 - Process and analyze
![[Pasted image 20240805144137.png]]

Data Lifecycle - 4 - Explore and visualize
![[Pasted image 20240805145155.png]]

Big Data & Analytics in GCP
![[Pasted image 20240805145402.png]]

Big DataFlow - Batch Ingest into BigQuery
- Use extra, transform, load (ETL) to load data into BigQuery
	- Dataprep: Clean and preapre data
	- Dataflow: Create data pipelines (and ETL)
	- Dataproc: Complex processing using Spark and Hadoop

Streaming Workflow - Enable Realtime Querying
- Query data in Realtime:
	- Pub / Sub and Dataflow: Analyze, aggregate and filter data before storing to BigQuery
	- For pre-defined time series analytics, storing data in BigTable gives you the ability to perform rapid analysis
	  
IOT
- IOT Core: Manage IoT (registration, authentication, and authorization) devices
	- Send / Receive messages / Real - time telemetry from / to IoT devices
- Pub / Sub: Durable message ingestion service (allows buffering)
- Dataflow: Processing data (ETL & more)
	- Alternative: Use Cloud Functions to trigger alerts
- Data Storage and Analytics:
	- Make IOT data available to mobile or web apps => Datastore
	- Execute pre-defiend time series queries => Bigtable
	- More complex or ad hoc analytics / Analysis => BigQuery

Data Lake - Single platform with combination of solutions for data storage, data management and data analytics

GCP Data Lakes - Storage and Ingestion
- Storage: Cloud Storage (low cost + durability + performance + flexible processing)
- Data Ingestion:
	- Streaming data - Cloud Pub / Sub + Cloud Dataflow
	- Batch - Transfer Service + Transfer Appliance + gsutil
- Processing and analytics:
	- Run in-place querying using SQL queries using BigQuery or (Hive on Dataproc)
- Data Mining and Exploration:
	- Clean and transform raw data with Dataprep
	- Use Cloud Datalab (data science libraries such as TesnorFlow and NumPy) for exploring

Question 1:

Which of these services can be used to clean data on-boarded from external sources?

- Cloud Datalab
    
- Cloud Dataprep - o
    
- Cloud Data Loss Prevention
    
- Cloud Dataflow

Which of these services can be used to mask, tokenize, and transform sensitive elements in your data stored in Cloud Storage, BigQuery, and Datastore?

- Cloud Datalab
    
- Cloud Dataprep
    
- Cloud Data Loss Prevention - o
    
- Cloud Dataflow

Question 3:

Which of these services can be used to build flexible batch and streaming pipelines?

- Cloud Datalab
    
- Cloud Dataprep
    
- Cloud Data Loss Prevention
    
- Cloud Dataflow - o

Question 4:

Which of these services enable you to run Jupyter notebooks to explore, analyze and visualize your data running Python programs and SQL queries?

- Cloud Datalab - o
    
- Cloud Dataprep
    
- Cloud Data Loss Prevention
    
- Cloud Dataflow

Question 5:

Which of these services can be used to create dashboards and visualization around data stored in BigQuery?

- Cloud Data Studio - o
    
- Cloud Data Catalog

Question 6:

Which of these represents an example batch ingest into BigQuery?

- Cloud Storage > Dataflow > BigQuery - o
    
- IOT Core > Pub/Sub > Dataflow > BigQuery

uestion 7:

Which of these represents a simple architecture to execute real-time simple pre-defined queries on a single table containing huge volumes of time series data that is continuously streamed in?

- Pub/Sub > Dataflow > BigQuery
    
- Pub/Sub > Dataflow > Bigtable - o

Question 8:

Which of these services is used as storage for Data Lake in Google Cloud Platform?

- Cloud Storage - o
    
- Cloud BigQuery
    
- Cloud Spanner