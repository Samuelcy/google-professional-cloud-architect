Cloud VPN
- Cloud VPN - Connect on premise to GCP network over internet
	- Implemented using IPSec VPN Tunnel
	- Traffic through internet (public)
	- Traffic encrypted using Internet Key Exchange protocol
- Two types of Cloud VPN solutions:
	- HA VPN (SLA of 99.99% service availability with two external IP addresses)
		- Only dynamic routing (BGP) supported
	- Classic VPN (SLA of 99.9% service availability, a single external IP address)
		- Supports static routing (policy-based, route-based) and dynamic routing using BGP
- Easy to establish: Does not need carrier circuits or contracts
- Go for Cloud VPN if
	- You want the network to encrypt traffic OR
	- You want a lower throughput, low cost solution OR
	- You are experimenting with connectivity between cloud on-premises

Cloud VPN - VPN Gateway, Peer Gateway, and Cloud router
- High-availability (HA) VPN
	- High availability (99.99 SLA, within region)
	- Needs a Cloud HA VPN gateway
		- Regional resources with two interfaces
		- Connects to an on-premises VPN gateway (or peer gateway) through VPN tunnels
- Classic VPN
	- No high availability
	- Needs a Google Compute Engine VPN gateway
- VPN gateway - Regional resource
- Cloud Router enables Dynamic Routing: Enables Automatic route update when network topology occurs

Cloud Interconnect
- High speed, highly available, low-latency private connection into Google Cloud from your company's on-premises network
- Dedicated Interconnect: Ideal if you need high-bandwidth connect for large data transfers
	- Minimum private connection speed of 10 Gbps
	- Takes time to establish
- Partner Interconnect: Ideal if you need a private connection with lower bandwidth needs
- Data exchange happens through a private network:
	- Communicate using VPC network's internal IP addresses from on-premise network
	- Reduce egress costs

Hybrid Connectivity - Remember
- When you connect networks, ensure that resources on the networks use different range of IP addresses!
- Always think: What will we do if things go wrong?
	- Have a fallback option if the primary connection from on-premise to GCP fails
		- Dedicated interconnect as primary
		- VPN as backup in case of failure
- Remember that there is third hybrid connectivity option:
	- Direct Peering: Connect customer network to google network using network peering
		- Direct path from on-premises network to Google service
		- Not a GCP Service
			- Lower level network connection outside of GCP
		- NOT Recommended:
			- Use Cloud Interconnect and Cloud VPN


Question 1:

Which of these can be used to on-premise network to GCP over the internet?

- Cloud VPN - o
    
- Cloud Interconnect

Question 2:

Which of these is a high speed (more than 10Gbps),  highly available, low-latency private connection into Google Cloud from your company’s on-premises network?

- Cloud VPN
    
- Cloud Interconnect - o

Question 3:

Which of these enables Enables Dynamic Routing (Automatic route update when network topology changes) for your Cloud VPN connections?

- VPN Gateway
    
- Peer Gateway
    
- Cloud Router - o