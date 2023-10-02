# ansible-vsphere
This is a playbook (deploy.yml) and accompanying roles that deploy VMware ESXi/vSphere to Dell PowerEdge Rx40 hardware.

The playbook will:
1) update the DRAC(s) to the current software available from Dell
2) configure a management host (usually the Ansible controller) to work from
3) setup an NFS server to share software to the ESXi nodes (controller)
4) customize the ESXi installation ISO image to self-install
5) install ESXi on all nodes
6) deploy vCenter onto the first node and create the vSphere datacenter and cluster

Customize the following files to your needs:
1) create a `hosts` file based on the `hosts-example` for your inventory
2) create a `group_vars/all.yml` file based on the `group_vars/all_yml.example` file
3) create a `host_vars/<hostname>` file, for each ESXi node, based on the `host_vars/host-example` file

NOTES:
1) the `deploy.yml` playbook will only update DRAC firmware when the extra_var `drac=true` is passed to it
2) the `deploy.yml` playbook will only wipe and re-install the ESXi nodes when the `wipe=true` extra_var is passed to it
