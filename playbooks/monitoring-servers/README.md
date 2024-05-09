# ............................................ GRAFANA ........................................................ #
Install and Configure Grafana with some little tweaks:

# Ubuntu Helpful Resource:                           
https://grafana.com/docs/grafana/latest/setup-grafana/installation/debian/

# Amazon Linux or RHEL or Fedora Helpful Resource:   
https://grafana.com/docs/grafana/latest/setup-grafana/installation/redhat-rhel-fedora/
https://www.youtube.com/watch?v=9fnvUdexm0Y
https://middlewaretechnologies.in/2024/01/how-to-install-and-configure-grafana-oss-using-ansible.html

# MacOSX Helpful Resource:                           
https://grafana.com/docs/grafana/latest/setup-grafana/installation/mac/

# Youtube Helpful Videos:                            https://www.youtube.com/watch?v=3id6l_BWdNA
# Install Release: stable
# Package Name: grafana         ('grafana' PACKAGE name is same for MacOSX, Ubuntu and Amazon)
# Service Name: grafana-server  ('grafana' SERVICE name is only for MacOSX while 'grafana-server' SERVICE name for Ubuntu and Amazon)
# Running Port: 3000
# Default Email or username: admin
# Default Password: admin
# New Password: password123
# CMD Version Check on Ubuntu and Amazon : grafana-server --version   -> Version 10.4.2
# CMD Version Check on MacOSX : grafana --version   -> Version 10.4.2

# Binary Check on Ubuntu and Amazon : which grafana-server    -> /usr/sbin/grafana-server
# Binary Check on MacOSX : which grafana           -> /opt/homebrew/bin/grafana

# ............................................ ALERTMANAGER ........................................................ #
# Install and Configure Alert Manager:

# Helpful Resource: 
https://www.youtube.com/watch?v=3id6l_BWdNA
https://github.com/Devops-Techstack/Ansible-RealTime-Projects/blob/main/Real_project_Ansible/roles/alertmanager/vars/main.yml
https://www.youtube.com/watch?v=Kzpm-rGAXos     (Systemd Deep-Dive)
https://www.youtube.com/watch?v=6Cz6A8P0B2U     (How To Create a Simple Systemd Service?)

# Step 1) Download alertmanager as a gz file 
https://prometheus.io/download/

# Step 2) Choose: 
Operating system: linux
Architecture: amd64 (amd64 means x86-64)
and then right click the link and copy 'link address' and provide it as a source in the task of the playbook. So we can download the .gz and extract it.

# Note:- When we will unarchive it there are two important files
1) alertmanager      (This is executable which we will copy in the bin directory)
2) alertmanager.yml  (This is the default configuration file we can customize this file for our own custom configuration)
# Note:- Because we are writing a service file for alertmanager and its best practice to create a system user and add it to a group which we can use in the service configuration file.

# Open the port on the server: alertmanager runs on Port: 9093

# ............................................ ALERTMANAGER ........................................................ #
