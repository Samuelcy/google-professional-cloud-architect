Kubernetes
- Provides cluster management (including ugprades)
	- Each cluster can have different types of virtual machines
- Provides all important container orchestration features:
	- Auto scaling, service discovery, load balancer, self healing, zero downtime deployments

Google Kubernetes Engine (GKE)
- Managed Kubernetes service
- Minimize operations with auto-repair (repair failed nodes) and auto-upgrade 
- Provides Pod and Cluster Autoscaling
- Enable cloud logging and cloud monitoring with simple configuration
- Uses container optimized Os, a hardened OS built by Google
- Provides support for persistent disk and local ssd

Autopilot mode - GKE
- Reduce operational costs un running kubernetes clusters
- provides hands off experience

GKE Cluster
- Cluster: Group of compute engine instances
	- Master nodes - Manages the cluster
	- Worker nodes - Run your workloads (pods)
- Master Node (Control plane) componets:
	- API server - Handles all communication for K8S cluster (from nodes and outside)
	- Scheduler - Devices placement of pods
	- Controler Manager - Manages deployments and replicat sets
	- etcd - Dsitrbuted database storing the cluster state
- Worker Node components:
	- Run your pods
	- Kubelet - Manages communication with master node(s)
![[Pasted image 20240717190324.png]]

Kubernetes - Pods
- Smallest deployable unit in Kubernetes
- A pod contains one or more containers
- Each Pod is assigned an ephemeral IP address
- All containers in a pod share:
	- Network
	- Storage
	- IP Address
	- Ports and
	- Volumes
- POD statuses: Running / Pending / Succeeded / Failed / Unknown

Kubernetes - Deployment vs Replica set
- A deployment is created for each microservice
	- kubectl create deployment ml --image=ml:v1
	- Depolymetn represents a microservice
	- Deployment manages new releases ensuring zero downtime
- Replica set ensures that a specific number of pods are running for a specific microservice version

Kubernetes - Service
- Each Pod has its own IP address
- Create Service
- Three types:
	- ClusterIP: Exposes service on a cluster-internal IP
	- LoadBalancer: Exposes Service externally using a cloud providers load balancer
	- NodePort: Exposes service on each Node's IP at static port (the node port)

Container Registry - Image Repository
- Container Registry - fully-managed container registry provided by GCP

![[Pasted image 20240717194409.png]]
![[Pasted image 20240717194547.png]]![[Pasted image 20240717195218.png]]

Question 1:

You want to deploy a complex microservices architecture using container orchestration. Which of these GCP services would you make use of?

- Google Kubernetes Engine - o
    
- App Engine
    
- Cloud Functions
    
- Cloud Run
  
A pod becomes unhealthy. Which of these will identify and replace the pod?

- Deployment
    
- Service
    
- ReplicaSet - o

Question 3:

How do we store sensitive configuration (passwords) in Kubernetes?

- ConfigMap
    
- Secrets - o
    
- Passwords
  
Question 4:

Which of these commands is used to connect to a Kubernetes Cluster?

- gcloud container clusters get-credentials - o
    
- kubectl get cluster credentials
  
  Question 5:

You want to deploy a new version of microservice without any downtime. Which of these approaches would you recommend?

- Delete the old deployment. Create a new deployment.
    
- Update the existing deployment with the image of a new version of the microservice. -o 
  

Question 6:

You have 3 instances of a microservice deployed to a Kubernetes Cluster. You want to enable auto-scaling for the microservice. You also want to automatically increase the number of nodes in the cluster if existing nodes are not sufficient. Which of these approaches would you recommend?

- Use `kubectl scale deployment` command to auto-scale pods and `kubectl container clusters update` to auto-scale cluster
    
- Use `gcloud scale deployment` command to auto-scale pods and `kubectl container clusters update` to auto-scale cluster
    
- Use `kubectl autoscale deployment` command to auto-scale pods and Use `gcloud container clusters update` command with --enable-autoscaling to auto-scale cluster - o