Computer Engine Features
- Create and manage lifecycle of VM 
-  Loading balancing and auto scaling
-  Attach storage and network storage to your VM instances
- Manage network connectivity and configuration

Compute Engine Machine Family
- Different machine families for different workloads
- General purpose (E2,N2,N2D,N1): Best price-performance ratio
	  - Web and application servers, small-medium databases, dev environments
- Memory Optimized (M2,M1): Ultra high memory workload 
- Compute Optimized: Compute intensive workloads
	- Gaming applications

Larger machine type = higher memory, disk and networking capabilities increase along with vCPUs

Image
- Public images: Provided and maintained by Google or Open source communities or third party vendors
- Custom images: Created by you for your projects (choose hardware, software etc)
  
Commands:
1. sudo su
2. apt update
3. apt install apache2
4. ls /var/www/html
5. echo "Hello World!"
6. echo "Hello World!" > /var/www/html/index.html
7. echo $(hostname)
8. echo $(hostname -i)
9. echo "Hello World from $(hostname)"
10. echo "Hello World from $(hostname) $(hostname -i)"
11. echo "Hello world from $(hostname) $(hostname -i)" > /var/www/html/index.html
12. sudo service apache2 start

Internal and External IP Address
- External Public IP are internet addressable
- Internet (private) Ip addresses are internal to a corporate network 
-  You can not have two resources with the same public (External) IP address
	- However, two different corporate networks can have resources with same Internal (private) IP address
- All VM instances are assigned at least one Internal IP address
- Creation of External IP addresses can be enabled for VM instances
	- When you stop a VM instance, external IP address is lost

Static IP can be switched from one VM instance to another VM instance
Static IP remains attached even if you stop the instance
You are billed for an Static IP when you are NOT using it as well

Startup Script
1. #!/bin/bash
2. apt update 
3. apt -y install apache2
4. echo "Hello world from $(hostname) $(hostname -I)" > /var/www/html/index.html
   
   
Simplify VM HTTP server setup

Bootstrapping: Install OS  patches or software when a VM is launched

Instance template - define machine type, images, labels, startup script

Q. Can you change the Machine Type (and the number of vCPUs and memory) of a VM?
- O | Yes. When it is stopped. 
- Yes. Even when it is running.
- No. You cannot
  
Q. Which of these is the preferred option to reduce the launch time of a VM instance?
- Startup script
- O | Custom Image
  
Q. How can you avoid specifying all the VM instance details every time you create a VM?

- O | Create an Instance Template
- Create a Custom Image
- Create a Startup Script

Q. What does 2 in the Machine Type e2-standard-2 represent?
- O | 2 vCPUs
- 2 GB Memory
- Machine Family


