SSH into Linux VMs - Options
- Compute Engine Linux VMs uses key-based SSH authentication
- Two options:
	- Metadata managed: Manually create and configure individual SSH keys
	- OS Login: manage SSH access without managing individual SSH keys!
		- Recommended for managing multiple users across instances or projects
- Windows instances use password authentication

SSHing into Linux VMs - Details
- Compute Engine Linux VMs
- Option 1: Console - SSH Button
- Option 2: Gcloud - gcloud computer ssh
- Option 3: Use customized ssh keys

Executing Shutdown Script on a GCE VM
- Execute commands before a GCE VM is stopped, terminated, or restarted
	- Perform cleanup or export of logs
	- Applicable for preemptible for non preemptible gce VMS
- Very similar to startup script
- 