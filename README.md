# cldemo-netq-vxlan

This demo repo is to be downloaded onto the oob-mgmt-server of cldemo-vagrant(<https://github.com/CumulusNetworks/cldemo-vagrant>) under 'cumulus' user. It assumes the rest of the network nodes are up and running, but have no configuration on them.

To execute the playbook to setup netq, type:

    ansible-playbook -s configure.yml

Once successfully run, you can type 'netq' to see the status of the various nodes. You can also type 'netq' by logging into any of the spine/leaf nodes.
Typing 'netq <TAB>' will show you options to try out. Some useful examples to get you going:

    netq check bgp
    netq check vlan
    netq show macs leaf01
    netq show changes between 1s and 2m
    ip route | netq resolve | less -R

To see VxLAN trace, ping 10.1.20.1 from server03. Then type:

    netq trace l2 44:38:39:00:00:28 vlan 20 from leaf01
