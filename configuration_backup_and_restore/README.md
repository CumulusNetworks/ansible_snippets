# Configuration Backup and Restore

These example playbooks can be used to perform a backup and restoration of configuration using the Network Command Line Utility (NCLU)

## Prereqs
* Ansible 2.0+
* Cumulus 3.3.0+

## Assumptions
This example was built to work with the [cldemo-vagrant](https://github.com/CumulusNetworks/cldemo-vagrant) reference topology.

## How to Run
1). Clone this repo.
```
git clone https://github.com/CumulusNetworks/ansible_snippets.git
cd ./ansible_snippets/configuration_backup_and_restore
```

## Backup Your Configurations
2). Run the Configuration Backup Playbook
```
cumulus@oob-mgmt-server:$ ansible-playbook configuration_backup.yml
```
At this point, the playbook will create a directory called configuration_storage with subdirectories for each switch. The directory for each switch will be populated with two files, one containing the NCLU commands required to restore the present state, and the other with the output of `net show config files` which will archive the flat files required to restore the state as well.

Two copies of the files will be created, one that is timestamped and another version which is always prepended with the name "current".

## Restore Your Configurations
3). Run the Configuration Restore Playbook
```
cumulus@oob-mgmt-server:$ ansible-playbook configuration_restore.yml
```
This playbook will restore your configurations using the NCLU commands prepended with the name "current"


