# cldemo-netq

This demo repo is to be downloaded onto the oob-mgmt-server of cldemo-vagrant
under 'cumulus' user. It assumes the rest of the network nodes are up and
running, but have no configuration on them.

To execute the playbook to setup netq, type:
ansible-playbook -s configure.yml
