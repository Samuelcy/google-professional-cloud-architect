Resource Hierarchy in GCP
- Organization > Folder > Project >Resources
- Resources are created in projects
- A Folder can contain multiple projects
- Organization can contain multiple folders

Resource Hierarchy - Recommendations for Enterprises
- Create separate project for different environments:
	- Complete isolation between test and production environments
- Create separate folders for each department:
	- Isolate production applications of one department from another
	- We can create a shared folder for shared resources
- One project per application per environment:

Billing Accounts
- Billing account is mandatory for creating projects
- Billing Account can be associated with one or more projects
- Two Types:
	- Self Serve: Billed directly to credit card or bank account
	- Invoice: Generate invoices (Used by large enterprises)

Managing Billing - Budget, Alerts, and Exports
- Setup a Cloud Billing Budget to avoid surprises:
	- Recommended configure Alerts
- Billing data can be exported (on a schedule)

IAM Best Practices
- Principle of Least Privilege - Give least possible privilege needed for a role
	- Basic Roles are not recommended
		- Prefer predefined roles when possible
	- Use service accounts with minimum privileges
		- Use different service accounts for different app / purposes
- Separation of Duties - Involve atleast 2 people in sensitive tasks:
	- Example: Have separate deployer and traffic migrator roles
- Constant Monitoring: Review Cloud Audit Logs to audit changes to IAM policies and access to Service Account keys
	- Archive Cloud Audit Logs in Cloud Storage buckets for long term retention
- Use Groups when possible

User Identity Management in Google Cloud
- Email used to create free trial account => "Super Admin"
	- Access to eveyrthing in your GCP organization, folders, and projects
	- Manage access to to other users using their Gmail Accounts
- However, this is not recommended for enterprises
- Option 1: Your enterprise is using Google Worksapce
	- Use Google Workspace to manage suers (groups etc)
	- Link Google Cloud Organization with Google Workspace
- Option 2: Your enterprise uses an Identity Provider on its own
	- Federate Google Cloud with your identity provider

Corporate Directory Federation
- Federate Cloud Identity or Google Workspace with your external identity provider (IdP) such as Active Directory or Azure Active Directory
- Enable Single Sign On:
	- 1. Users are redirected to an external IdP to authenticate
	- 2. When users are authenticated, SAML assertion is sent to Google  Sign - In

IAM Members / Identities
- Google Account - Represents a person (an email address)
- Service account - Represents an application account (Not person)
- Google group - Collection - Google & Service Accounts
	- Has an unique email address
	- Helps to apply access policy to a group
- Google Workshop domain: Google Workspace provides collaboration services for enterprises:
	- Tools like Gmail, Calendar, Meet, Chat, Drive, Docs etc are included
	- If your enterprise is using Google Workspace, you can manage permissions using your Google Workspace domain
- Cloud Identity Domain - Cloud Identity is an identity as a service (IDaaS) solution that centrally manages users and groups
	- You can use IAM to manage access to resources for each Cloud Identity account
![[Pasted image 20240730111358.png]]
Organization Policy Service
- How to enable centralized constraints on all resources created in an Organization?
	- Configure organization Policy
	- Example: Disable create of Service Accounts
	- Example: Allow / Deny creation of resources in specific regions
- Needs a role - Organization Policy Administrator
- (Remember) IAM focuses on Who
	- Who can take specific actions on resource?
- (Remember) Organization policy focuses on What
	- What can be done on specific resources

Resource Hierarchy & IAM policy
- IAM Policy can be set at any level of the hierarchy
- Resoruce inheir the policies of All parents
- The effective policy for an resource is the union of the policy on that resource and its parents
- Policy inheritance is transitive:
	- ex. organization policies are applied at resource level
- You can't restrict policy at lower level if permission is given at a higher level

Cloud BigQuery Role


Corporate Directory Federation
- Federate Cloud Identity or Google Workspace with your external identity provider (IdP) such as Active Directory or Azure AD
- Enable Single Sign On:
	- 1: Users are redirected to an external IdP to authenticate
	- 2: When users are authenticated, SAML aseertion is sent to Google Sign-In
- Examples:
	- Use Identity as a service (IDaas) such as Okta as IdP (Identity provider)
	- Use Active directory as IDP
	- Use Azure AD as IdP
![[Pasted image 20240730112811.png]]Which of these represents the resource hierarchy in GCP?

- Organization > Projects > Folders > Resources
    
- Organization > Folders > Resources > Projects
    
- Organization > Folders > Projects > Resources - o
    
- Projects > Organization > Folders >  Resources

Question 2:

Which of these can be used to synchronize users and groups from Active Directory to Cloud Identity?

- Google Cloud Directory Sync - o
    
- Active Directory Federation Services (AD FS)