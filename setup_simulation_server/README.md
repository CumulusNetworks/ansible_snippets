# Setting up an Ubuntu 16.04 Server for Simulation

These steps are an automated approach to the manual documentation outlined here:
[https://docs.cumulusnetworks.com/display/VX/Vagrant+and+Libvirt+with+KVM+or+QEMU](https://docs.cumulusnetworks.com/display/VX/Vagrant+and+Libvirt+with+KVM+or+QEMU)

The ideal simulation server has the following parameters:
* ~80GB+ of RAM
* As many CPU cores as you can provide
* ~20GB+ of Disk space
* Has Ubuntu 16.04 preinstalled
* Has Internet access

To run the playbook add your simulation server to the "hosts" file used by ansible to define the inventory.
Add modify the playbook to define the `host:` line as the server to be used for simulation.

```
user@someserver# cd ./ansible_snippets/setup_simulation_server
user@someserver# ansible-playbook ./setup_simulation_server.yml
```
