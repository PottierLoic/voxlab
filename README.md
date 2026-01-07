Voxlab is my personal home lab setup managed with Ansible.
I simply use this repository to save and version control my Ansible playbooks and related configuration files.
This should not be used as a ready-to-use solution, it simply is a reference for my own setup.

# Requirements

Two servers/VMs:
- one to use ansible from (control node)
- one to deploy the lab to (managed node)

the control node should have ansible installed.
the managed node should simply ssh accessible from the control node with sudo privileges.

# Setup

Deploy playbook:
```bash
ansible-playbook -i inventory.ini site.yml -K
```

Add proxy hosts to nginx-proxy-manager (raw_conf/npm-proxy-hosts) on ip:81
Add pihole dns (raw_conf/pihole-dns) on ip:8053
Configure dns on devices to point to the lab (only the lab, no other dns)

At this point dashboard.voxlab.lan should be accessible as well as other services configured in the playbook.

Configure the monitor in uptime kuma for eachh service.
If they do not correspond, modify the slugs in the paybook and re-deploy to get uptime-kuma widgets working in the dashboard.


### services to add:

- memos: note taking app
- mealie or tandor: meal planning
- portainer
- uptime kuma: service status to add on homepage
- dashdot: cpu, ram, disk... infos
