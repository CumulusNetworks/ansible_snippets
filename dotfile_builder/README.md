# DOT file Builder

This simple Ansible script will create a [topology.dot](https://docs.cumulusnetworks.com/display/DOCS/Prescriptive+Topology+Manager+-+PTM#PrescriptiveTopologyManager-PTM-configuringConfigurePTM) file which can be used for PTM or to create simulations with a tool like [topology_converter](https://github.com/CumulusNetworks/topology_converter).

*Example*
```
cumulus@oob-mgmt-server:~$ ansible-playbook ./create_graph.yml 
```

The playbook will evaluate the Ansible Facts and LLDP information of each node in order to build a graph of the environment. This graph will be output for each node and will automatically prune duplicate interfaces.

Useful for creating a simulation of an existing environment.
