# cldemo-netq-vxlan

This demo repo is to be downloaded onto the oob-mgmt-server of cldemo-vagrant(<https://github.com/CumulusNetworks/cldemo-vagrant>) under 'cumulus' user. It assumes the rest of the network nodes are up and running, but have no configuration on them.

If you had already run a different configuration playbook (for example the l2 or l3 setup) on this setup, clear out all that using the command:

    ansible-playbook -s reset.yml

To execute the playbook to setup netq, type:

    ansible-playbook -s configure.yml

Once successfully run, you can type 'netq' to see the status of the various nodes. You can also type 'netq' by logging into any of the spine/leaf nodes.
Hitting TAB after typing 'netq' will show you commands available along with help text. Some useful examples to get you going:

    netq check bgp
    netq check vlan
    netq show ip routes 10.254.0.6 origin
    netq show macs leaf01
    netq show changes between 1s and 2m
    ip route | netq resolve | less -R

To see VxLAN trace, log into server01 and ping 10.253.20.3. Lookup the MAC address for 10.253.0.3 (show ip neighbor). Then exit server01 and type (assuming 44:38:39:00:00:65 is the MAC of 10.253.20.3):

    netq trace l2 44:38:39:00:00:65 vlan 20 from leaf01
