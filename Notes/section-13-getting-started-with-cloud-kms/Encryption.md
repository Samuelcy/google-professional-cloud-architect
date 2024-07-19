Data States
- Data at rest: Stored on a device or a backup
	- Examples: data on a hard disk, in a database, backups and archives
- Data in motion: being transferred across a network
	- Also called Data in transit
	- Examples
		- Data copied from on permise to cloud storage
		- An applciation talking to a database
		- Two Types
			- In and out of cloud (from internet)
			- Within cloud
- Data in use: active data processed in a non-persistent state
	- Example: Data in your RAM

Encryption
- First law of security: Defense in Depth
- Typically enterprises encrypt all data
	- Data on your hard disks
	- Data in your databases
	- Data on your file servers
- Is it suffience if you encrypt data at rest?
	- No. Encrypt data in transit - between application to database as well

Symmetric Key Encryption
- Symemtric encryption algorithmsn use teh same key for encryption and decryption
- Key Factor 1: Choose the right encryption algorihtmn
- Key Factor 2: How do we secure the encryption key
- Key Factor 3: How do we share the encryption key

Asymmetric Key Encryption
- Two Keys: Public and Private Key'
- Also called Public Key Cryptogrpahy
- Encrypt data with Public Key and decrypt with Private Key
- Share Public Key with eveyrbody and keep the Private Key with you (its private)
-

Cloud KMS
- Create and manage cryptographic keys (symmetric and asymmetric)
- Control their use in your applications and GCP services
- Provides an API to encrypt, decrypt, or sign data
- Use existing cryptographic keys created on premises
- Integrates with almost all GCP services that need data encryption
	- Google-managed key: Configuration required
	- Customer-managed Key: Use key from KMS
	- Customer-supplied key: Provide your own key