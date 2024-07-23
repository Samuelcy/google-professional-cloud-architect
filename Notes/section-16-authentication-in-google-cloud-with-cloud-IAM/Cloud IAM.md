IAM - Identity and access management

Typical iam
- Resources in the cloud(database), identities (human and nonhuman). identites need to contact these resources

Cloud IAM
- Authentication - is it the right user?
- Authorization - right access?
- Provides granular control, limit a single user to perform a single action on a specific cloud resources from a specific ip address during a specific time window

Cloud IAM Example
- Google Cloud IAM 
	- Roles: A set of permissions (to perform specific actions on specific resources)
		- Roles do not know about members. Its all about permissions
	- Policy: Assign (or bind) a role to a member
- 1. Choose a role with right permissions (Ex: Storage Object Admin)
- 2. Create Policy binding member (your friend) with role (permissions)
- IAM in AWS is very different from GCP (Forget AWS IAM & Start Fresh)

IAM - Roles
- Roles are permissions
	- Perform set of actions on some set of resources
- Three Types:
	- Basic Roles (or Primitive roles) - Owner / Editor / Viewer
		- Viewer (roles.editor) - Viewer + Edit actions
		- Owner (roles.owner) - Editor + Manage Roles and Permissions + Billing
	- Predefined Roles - Fine grained roles predefined and maanged by Google
		- Different roels for difrent purposes
		- Examples: Storage Admin, Storage Object Admin, Storage Object Viewer, Storage Object Creator
	- Custom Roles - When predefined roels are not sufficient, you can create your own custom roles

IAM - Concepts
- Member - Who?
- Roles: Permissions (What actions? What resources)
- Policy: Assign permission to members
	- Map Roles (what?), members (who?), and conditions (Which resources?, when?, from where?)
	- Remember: Permissions are NOT directly assigned to Member
		- Permissiosn are represented by a Role
		- Member gets permissions through Role!
- A Role can have multiple permissions
- You can assign multiple roles to a member


IAM policy
- Roles are assigned to uses through IAM policy documents
- Represented by a policy object
	- Policy object has list of bindings
	- A binding, binds a role to list of members
- Member type is identified by prefix:
	- Example: user, serviceaccount, group or domain

Service Accounts
- Scenario: An application on a VM needs access to cloud storage
	- DO\on't use personal credentials
- Use service accounts
	- Identified by an email address
	- Does not have password
- Service account types:
	- Default service account - Automatically created when some services are used
		- (Not recommended) Has editor role by default
	- User managed - User created
		- (Recommended) Provides fine grained access control
	- Google-managed service accounts - Created and managed by Google
		- Used by GCP to perform operations on user's behalf
		- In general, we DO NOT need to worry about them

Use case1: VM <-> Cloud Storage
1. Create a service account role with the right permissions
2. Assign service account role to VM instance
- Uses google cloud managed keys
	- Key generation and use are automatically handled by IAM when we assign a service account to the instance
	- Automatically rotated
	- No need to store credentials in config files
- Do NOT delete service accounts used by running instances: 
	- Applications running on those instances will lose access

Use case 2: On Prem <-> Cloud Storage (Long lived permission)
- You cannot assigned Service Account directly to an On Prem App
1.  Create a Service Account with right permissions
2. Create a Service Account User managed Key
3. Make the service account key file accessible to your applicaiton
4. Use Google Cloud Client Libraries

Use case 3: On Prem <-> Google CLoud APIs (short lived)
- Make calls from outside GCP to Google Cloud APIs with short lived permissions
	- Few hours or shorter
	- Less risk compared to sharing service account keys
- Credential Types:
	- OAuth 2.0 access tokens
	- OpenID Connect ID tokens
	- Self-signed JSON Web Tokens (JWTs)
- Examples:
	- When a member needs elevated permissions, he can assume the service account role (Create OAuth 2.0 access token for service account)
	- OpenID Connect ID tokens is recommended for service to service authentications
![[Pasted image 20240722144413.png]]

ACL (Access Control Lists)
- ACL: Define who has access to your buckets and objects, as well as whnat level of access they hav
- How is it different from IAM
	- IAM permissions apply to all objects within a bucket
	- ACLs can be used to customized specific accesses to different objects
- User gets access if he is allowed by IAM or ACL
- Use IAM for common permissions to all objects in a bucket
- Use ACLs if you need to customize access to individual objects

Access Control - Overview
- Two types
	- Uniform (Recommended) - Uniform bucket level access usign IAM
	- Fine-grained - Use IAM and ACLs to control access:
		- Both bucket and individual object level permissions
- Use uniform access when all users have same level of access across objects in a bucket
- Fine grained access with ACLs can be used when you need to customize the access at an object level
	- Give a user specific access to edit specific objects in a bucket

Cloud Storage - Signed URL
- Allow a user limited time access to your objects
	- Users do not need Google accounts
- Use signed URL funcitonality
	- A URL that gives permissions for limited time duration to perform specific actions
![[Pasted image 20240722150035.png]]
Question 1:

Which one of these is NOT a basic role?

- Owner
    
- Editor
    
- Reader - o
    
- Viewer

Question 2:

TRUE or FALSE: You should always use Basic Roles to provide access to your users

- True
    
- False - o

Question 3:

An on-premise application needs access to files in a Cloud Storage bucket. Which of these approaches would you recommend?

- Use a Service Account (Google Cloud-managed keys)
    
- Use a Service Account with a User-Managed Key - o
    
- Use Signed URLs

Question 4:

Permission is allowed by IAM but NOT by ACL. Will the user be able to access the object?

- Yes. It's sufficient if either IAM or ACL allows access. - o
    
- No. You need to be allowed by both IAM and ACL.