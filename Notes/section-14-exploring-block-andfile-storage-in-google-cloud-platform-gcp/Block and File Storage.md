
Block Storage
- Harddisks
- One block storage device can be connected to one virtual server
- You can connect multiple different block storage devices to one virtual server
- Used as:
	- Direct-attached storage (DAS) - Similar to hard disk
	- Storage Area Network (SAN) - High-speed network connecting a pool of strage devices

File Storage
- Media workflows need huge shared storage for supporting processes like video editing
- File shares shared by several virtual servers

GCP - Block storage and file storage
- Block Storage
	- Persistent Disks: Network Block Storage
		- Zonal: Data replicated in one zone
		- Regional: Data replicated in multiple zone
	- Local SSDs: Local Block Storage
- File Storage
	- Filestore: High performance file storage

GCP - Block Storage
- Two types
	- Local SSDs
	- Persistent Disks
- Local SSDs are physically attached to the ghost of the VM instance
	- Temporary data
	- Lifecycle tied to VM instance
- Persistent Disks are network storage
	- More durable
	- Lifecycle NOT tied to VM instance

Local SSDs
- Physically attached to the host of VM instance
	- Provide high IOPS and very low latency
	- But ephermeral stoarge - Temporary data (Data persists only until isntance is running)
		- Enable live migration for data to survive maintence events
	- Data automatically encrypted
		- However, you cannot configure encryption keys
	- Lifecycle tied to VM instance
	- Only some machine types support Local SSDs
	- Supports SCSI and NVMe interfaces
- Remember:
	- Choose NVMe-enabled and multi-queue SCSI images for best performance
	- Larger Local SSDs (more storage), more vCPUs (attached to VM) => Even Better Performance
- Advantages
	- Very fast I/O. higher throuhgput and lower latency
	- Ideal for uses cases needing high IOPs while storing temporary information
- Disadvantages
	- Ephemeral storage: Lower durability, lower availability, lower flexibility
	- You cannot detach and attach it to another VM instance

Persistent Disks (PD)
- Network block storage attached to your VM instance
- Provisioned capacity
- Very flexible
	- Increase size when you need it - when attached to VM instance
	- Perforamnce scales with size
- Independent lifecycle from VM instance
	- Attach / Detach from one VM instance to another
- Options: Regional and Zonal
	- Zonal PDs replicated in single zone. Regional PDs replicated in 2 zones in same Region
	- Typically regional PDs are 2x the cost of Zonal PDs
- Use case: Run your custom database
![[Pasted image 20240719104824.png]]![[Pasted image 20240719105137.png]]

Persistent Disks - Snapshots
- Take point in time snapshots of your Persistent Disks
- You can schedule snapshots ( configure a schedule)
- Snapshots can be multi regional and regional
- You can share snapshots across projects
- You can crate new disk and instances from snapshots
- Snapshots and incremental
	- Deleting a snapshot only deletes data which is not needed by other snapshots
- Keep similar data together on a Persistent Disk:
	- Separate your operating system, volatile data and permanent data
	- Attach multiple disks if needed
	- This helps to better organize your snapshots and images

Persistent Disks - Snapshots - Recommendations
- Avoid taking snapshots more often than once an hour
- Disk volume is available for use but Snapshots reduce performance
- Creating snapshots from disk is faster than creating from images:
	- But creating disks from image is faster than creating from snapshots
	- Recommended if you are repeatedly creating disks from a snapshot
		- Create an image from snapshot and use the image to create disks
- Snapshots are incremental
	- You don't lose data by deleting older snapshots
	- Deleting a snapshot only deletes data which is not needed by other snapshots. Recommended do not hesitate to delete unnecessary snapshots

Mounting a Data Persistent Disk on a GCE VM
- Steps to attach a newly created Persistent Disk with an already running VM:
	- A: Attach Disk to running or stopped VM
		- gcloud compute instances attach-disk INSTANCE_NAME --disk DISK_NAME
	- B: Format the disk
		- 1. List disks attached to your VM
			- sudo lsblk
		- 2. Format to file format of your choice (ex. ext4 file system)
			- sudo mkfs.ext4 -m 0 -E lazy_itable_init=0,lazy_journal_init=0,discard /dev/sdb
	- C: Mount the disk
		- 1. Create the directory to mount to
			- sudo mkdir -p /mnt/dsks/MY_DIR
		- 2. Mount the disk
			- sudo mount -o discard,defaults /dev/sdb /mnt/disks/MY_DIR
		- 3. Provide permissions

Resize Data Persistent Disks
- Step 1: Resize the disk
	- gcloud compute disks resize DISK_NAME --size DISK_SIZE
- Step II: Take a snapshot (just for backup incase things go wrong)
- Step III: Resize the file system and partitions

Playing with Machine Images
- Remember Machine Image is different from Image
- Multiple disks can be attached with a VM:
	- One boot disk (Your OS runs from Boot Disk)
	- Multiple Data Disks
- An image is created from the boot Persistent Disks
- However, a machine image is created from a VM instance:
	- Machine image contains everything you need to create a VM instance:
		- Configuration
		- Metadata
		- Permissions
		- Data from one or more disks
- Recommended for disk backups, instance cloning and replication
![[Pasted image 20240719113300.png]]

![[Pasted image 20240719113534.png]]

Cloud Filestore
- Shared cloud file storage
	- Supports NFSv3 protocol
	- Provisioned Capacity
- Suitable for high performance workloads
	- Up to 320 TB with throughput of 16GB/s and 480k IOPS
- Supports HDD (general purpose) and SSD (performance - critical workloads)
- Use cases: file share, media workflows and content management

Review - Global, Regional and Zonal Resources
- Global
	- Images
	- Snapshots
	- Instance templates (Unless you use zonal resources in your temnplates)
- Regional
	- Regional managed instance groups
	- Regional persistent disks
- Zonal
	- Zonal managed instance groups
	- Instances
	- Persistent disks
		- You can attach a disk only to instances in the same zone as the disk
![[Pasted image 20240719114107.png]]
Question 1:

Which one of these options can help you to increase the performance of a Persistent Disk volume?

- Increase size. But you have to disconnect the persistent disk from the VM when you increase size.
    
- Increase size while a Persistent Disk is connected to the VM - o

Question 2:

Which of these steps are needed to use a newly created Data Persistent Disk  (PD) from an already running GCE VM?

- Attach PD to VM instance(You don't need to Format or Mount)
    
- Stop the VM instance. Attach PD to VM. Format the disk. Mount the disk. Start the VM instance.
    
- Attach PD to VM instance. Format the disk. Mount the disk. - o

Question 3:

What of these steps would you recommend to increase the size of a data persistent disk (PD) attached to a running VM?

- Resize the disk. Resize file system using resize2fs or xfs_growfs based on the file system. VM restart is NOT needed. - o
    
- Stop the VM instance. Resize the disk. Resize file system using resize2fs or xfs_growfs based on the file system. Start the VM instance.

Question 4:

Which of these block storage options would you recommend for applications needing very fast disk IOPS with ephemeral data?

- Persistent Disks
    
- Local SSDs - o
    
- Filestore