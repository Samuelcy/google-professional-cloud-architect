Cloud Storage
- Most popular, very flexible & inexpensive storage service
	- Serverless: Autoscaling and infinite scale
- Store large objects using a key-value approach
	- Treats entire object as a unit 
	- Also called Object Storage'
- Provides REST API to access and modify objects
- Store all file types - text, binary, backup & archives:
	- Media files and archives, Application packages and logs 
	- Backups of your databases or storage devices
	- Staging data during on-premise to cloud database migration

Cloud Storage - Objects and Buckets
- Objects and stored in buckets
	- Bucket names are globally unique
	- Bucket names are used a part of object URLs => Can contain ONLY Lower case letters, numbers, hyphens, underscores and periods
	- 3-63 characters max. Can't start with goog prefix or should not contain cgoogle
	- Unlimited objects in a bucket
	- Each subejct is associated with a project
- Each object is identified by a unique key
	- Key is a unique in a bucket
- Max object size is 5TB
	- But you can store unlimited number of such objects
![[Pasted image 20240719124549.png]]

Features across Storage Classes
- High durability
- Low latency
- Unlimited storage
	- Autoscaling 
	- No minimum object size
- Same APIs across storage classes
-
Object Versioning
- Prevents accidental deletion & provides history
	- Enabled at bucket level
		- Can be turned on/off at anytime
	- Live version is the latest version
		- If you delete live object, it becomes noncurrent object version
		- If you delete noncurrent object version, it is deleted
	- Older versions are uniquely identified by (object key + a generation number)
	- reduce costs by deleting order (noncurrent) versions

Object Lifecycle Management
- Files are frequently accessed when they are created
	- Generally usage reduces with times
	- How do you save costs by moving files automatically between storage classes?
		- Solution: Object lifecycle managemetn
- Identify objects using conditions based on:
	- Age, Created Before, isLive, MatchesStorageClass, NumberOfNewVersion etc
	- Set multiple conditions: all conditions must be satisfied for action to happen
- Two kinds of acitons:
	- SetStorageClass actions (change from one storage to another)
	- Deleting actions (deletes objects)
- Allowed Transitions:
	- (Standard ot Multi-Regional or Regional) to (Nearline or Coldline or Archive)
	- Nearline to (Coldline to Archive)
	- Coldline to Archive

Cloud Storage - Encryption
- (Default) Cloud storage encrypts data on the server side
- Server-side encryption: Performed by GCS after it receives data
	- Google-managed - Default (No configuration needed)
	- Customer-managed - Keys managed by customer in Cloud KMS
	- Customer-supplied - Customer supplies the keys with every GCS operation
		- Cloud storage does not store the key
		- Customer is responsible for storing and using it when making API calls
- Optional Client - Side encryption - ENcryption peformed by customer before upload
	- GCP does not know abotu the keys used
	- GCP is not involved in encryption or decryption

Metadata
- Each object in cloud storage can have metadata associated with it
	- Key Value Pairs ex: storageClass: STANDARD
	- Fixed-key metadata: Fixed key - Changing value
	- Custom metadata: You can define your own keys and values
	- Non-editable metadata: You cannot edit these directly
		- Storage class of the object, customer-managed encryption keys etc

Cloud Storage Bucket Lock - Meet Compliance Needs
- Configure data retention policy with retention period:
	- Objects in the bucket can only be deleted or replaced once their age is greater than the retention period
- You can set it while creating a bucket or at a later point in time
	- Applies automatically to existing obejcts in the bueckt
- Once a retention policy is locked
	- You cannot remove retention policy or reduce retention period
	- You cannot delete the bucket unless all obejcts in bucket have age greater than retention period

Transferring data from on premises to cloud
- Most popular data destination is Google Cloud Storage
	- Options:
		- Online Transfer: Use gsutil or API to transfer data to Google Cloud Storage
			- Good for one time transfers
		- Storage Transfer Service: Recommended for large-scale (petabytes) online data transfers from your private data centers, AWS, Azure, and Google Cloud
			- Reliable and fault tolerant - continues where it left off
		- Storage Transfer Service vs gsutil:
			- gsutil is recommended only when you are transferring less than 1 TB from on-premises or another GCS bucket
			- Storage Transfer Service is recommended if either of the conditions is met:
				- Transferring more than 1 TB from anywhere

Migrating Data with Transfer Appliance
- Transfer Appliance: Copy, chip and upload data to GCS
	- Recommended if your data size is greater than 20TB
		- or online transfer takes > 1 week
	- Process
		- Request an appliacem, upload your data, ship your appliance back, google uploads the data
	- Fast copy (40 Gbs)
	- Order multiple devices

Understanding Cloud Storage Best Practice
- Avoid use of sensitive info in bucket or object names
- Store data in the closest region (to your users)
- Ramp up request rate gradually

![[Pasted image 20240719140127.png]]

Question 1:

You want to ensure that log files in a Cloud Storage bucket are not modified for at least 2 years after creation (Compliance needs). How would you implement this?

- Configure Life cycle policy on the bucket
    
- Configure the Retention policy on the bucket and lock it - o
    
- Use Bucket ACL's
  
Question 2:

You are currently using the Standard storage class to store all files in a Cloud Storage bucket. The files would be frequently accessed for the first 5 days. After that, the files will not be accessed at all. However, you want to retain files for compliance. How would you implement this?

- Configure Life cycle policy on the bucket - o
    
- Configure the Retention policy on the bucket and lock it
    
- Use Bucket ACL's
  
Question 3:

Which of these tools would you recommend to transfer data from Amazon S3 to Cloud Storage?

- gsutil
    
- Cloud Storage Transfer Service - o
  

Question 4:

You want to store your encryption keys on-premises, encrypt data on-premises and send encrypted data to Cloud Storage. Which of these approaches would you recommend?

- Customer-managed encryption keys
    
- Customer-supplied encryption keys
    
- Client Side Encryption - o

Question 5:

You want to simplify the management of your encryption keys. You want to use a Google Cloud Managed Service to manage your keys and use them to encrypt your Cloud Storage objects. Which of these approaches would you recommend?

- Customer-managed encryption keys - o
    
- Customer-supplied encryption keys
    
- Client-Side Encryption

Question 6:

Cache-Control, Content-Disposition, and Content-Type are examples of:

- Fixed-key metadata - o
    
- Custom metadata
    
- Non-editable metadata

Question 7:

You want to transfer 100 TB of data from on-premise to Cloud Storage. Which of these options would you recommend?

- Use Transfer Appliance - o
    
      
- Use Cloud Storage Transfer Service

Question 8:

TRUE or FALSE: Cloud Storage is serverless and auto-scaling.

- TRUE - o
    
- FALSE

Question 9:

TRUE or FALSE: Cloud Storage supports partial updates for an object

- TRUE
    
- FALSE - o

Question 10:

Which Cloud Storage - Storage Class would you recommended for data expected to be accessed once in a quarter?

- Standard
    
- Nearline
    
- Coldline - o
    
- Archive

Question 11:

Which feature of Cloud storage can be used to avoid accidental deletion of files?

- Object Versioning - o
    
- Object Backup
    
- Lifecycle Policy
    
- Retention Policy

Question 12:

How do you provide time-limited read or write access to objects in a Cloud Storage Bucket?

- Signed Object
    
- Signed URL -o
    
- Use IAM
    
- Use ACLs