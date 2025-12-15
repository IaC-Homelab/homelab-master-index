1. Update `/etc/network/interfaces` with static IP
2. Update `/etc/hosts` with new host IPs
3. Remove all hosts from cluster
	* `pvecm delnode proxmox2`
4. Readd all hosts to cluster
	* `pvecm add `