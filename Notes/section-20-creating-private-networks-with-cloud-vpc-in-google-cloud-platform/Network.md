Need for Google Cloud VPC
- Corporate network provides a secure internal network protecting your resources, data and communication from external users
- How do you do create your own private network in the cloud?
	- Enter Virtual Private Cloud (VPC)

Google Cloud VPC (Virtual Private Cloud)
- Your own isolated network in GCP cloud
	- Network traffic within a VPC is isolated (not visible) from all other Google Cloud VPCs
- You control all the traffic coming in and going outside a VPC
- (Best Practice) Create all your GCP resources (compute, storage, databases etc) within a VPC
	- Secure resources from unauthorized access AND
	- Enable secure communication between your cloud resources
- VPC is a global resources & contains subnets in one ore more region
	- (REMEMBER) Not tied to a region or a zone. VPC resources can be in any region or zone!

Need for VPC Subnets
- Different types of resources are created on cloud - databases, computer etc
	- Each type of resources has its own access needs
	- Load Balancers are accessible from internet (public resources)
	- Databases or VM instances should NOT be accessible from internet
		- Only applications within your network (VPC)  should be able to access them (private resources)
- How do you separate public resources from private resources inside a VPC?
	- Create separate Subnets!
- (Additional Reason) You want to distribute resources across multiple regions for high availability

VPC Subnets
- (Solution) Create different subnets for public and private resources
	- Resources in a public subnet CAN be accessed from internet
	- Resources in a private subnet CANNOT be accessed from internet
	- BUT resources in public subnet can talk to resources in private subnet
- Each Subnet is created in a region

Creating VPCs and Subnets
- By default, every project has a default VPC
- You can create YOUR own VPCs:
	- Option 1: Automode VPC network:
		- Subnets are automatically created in each region
		- Default VPC created automatically in the project uses auto mode!
	- Option 2: Custom mode VPC network:
		- No subnets are automatically created
		- You have complete control over subnets and their IP ranges
		- Recommended for Production
- Options when you create a subnet:
	- Enable Private Google Access - Allows VM's to connect to Google API's using private IP's
	- Enable FlowLogs - To toruble shoot any VPC related network issues

CIDR (Classless Inter-Domain Routing) Blocks
- Resources in a network use continous IP addresses to make routing easy
- How do you express a range of addresses that resources in a network can have?
	- CIDR block
- A CIDR block consists of a starting IP address (69.208.0.0) and a range (/28)


Firewall Rules
- Configure Firewall rules to control traffic going in or out of the network:
	- Stateful
	- Each firewall rule has priority (0-65535) assigned to it
	- 0 has highest priority. 65535 has least priority
	- Default implied rule with lowest priortiy (65535)
	- Default implied rule with lowest priority (65535)
		- Allow all egress
		- Deny all ingress
		- Default rules can't be adeleted
		- You can override fault rules by defining new rules with priority 0-65534
	- Default VPC had 4 additional rules with priortiy 65534
		- Allow incoming traffic from VM instance in same network (default allow internal)
		- Allow incoming TCP traffic on port 22 (SSH) default-allowssh
		- Allow incoming TCP traffic on port 3389 (RDP) default-allow-rdp
		- Allow incoming ICMP from any source on the network default-allow-icmp

Firewall Rules - Ingress and Egress Rules
- Ingress Rules: Incoming traffic from outside to GCP targets
	- Target (defines the destination): All instances or instances with TAG/SA
	- Source (defines where the traffic is coming from): CIDR instances with TAG/SA
- Egress Rules: Outgoing traffic to destination from GCP targets
	- Target (defines the source): All instances or instances with TAG/SA
	- Destination: CIDR Block
- Along with each rule, you can also define:
	- Priority - Lower the number, higher the priority
	- Action on match - Allow or Deny traffic
	- Protocol - ex. TCP or UDP or ICMp
	- Port - Which port?
	- Enforcement status - Enable or disable the rule

Firewall Rules - Best Practice
- Use network tags and control allowed traffic into a VM using firewall rules
- Ensure that firewall rule allow the right kind of traffic:
	- Only allow traffic from load balancing into VM instances

Shared VPC
- Scenario: Your organization has multiple projects. You want resources in different projects to talk to each other?
- Enter Shared VPC
	- Created at organization or shared folder level (Access Needed: Shared VPC Admin)
	- Allows VPC network to be shared between projects in same organization
	- Shared VPC contains one host project and multiple service projects:
		- Host Project - Contains shared VPC network
		- Service Projects - Attached to host projects
- Helps you achieve separation of concerns:
	- Network administrators responsible for Host projects and resource users use Service Project

VPC Peering
- Scenario: How to connect  VPC networks across different organizations?
- Enter VPC Peering
	- Networks in same project, different projects and across projects in different organizations can be peered
	- All communication happens using internal IP addresses
		- Highly efficient because all communication happens inside Google network
		- Highly secure because not accessible from Internet
		- No data transfer charges for data transfer between services
	- (Remember) Network administration is not changed:
		- Admin of one VPC do not get

Question 1:

Which of these options would you enable on a subnet to allows VM's in a subnet to connect to Google APIs using private IPs?

- Enable Private Google Access - o
    
- Enable FlowLogs

Question 2:

You are making use of the default firewall rules. You want to allow only HTTPS outbound calls from your VM instances. You want to disable all other outbound traffic. Which of these options would you choose?

- Create an egress rule with priority 65000 to deny all traffic
    
- Create an egress rule with priority 1000 to allow HTTPS traffic (port 443)
    
- Both - o

Question 3:

Your organization has multiple projects. How do you allow resources in multiple projects to talk with internal IPs securely and efficiently?

- Shared VPC - o
    
- VPC Peering

Question 4:

You want to enable secure communication between two different VPC networks belonging to different organizations. Which of these options would you recommend?

- Shared VPC
    
- VPC Peering - o