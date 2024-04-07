# PRE - check all the users and groups
tail /etc/passwd
groups simone

# create a user and add it to a root group via playbook

# POST - check all the users and groups
tail /etc/passwd
groups simone

# check sudoers file on each server.
sudo ls -alh /etc/sudoers.d/