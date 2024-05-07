<!-- GRAFANA SERVER -->

# Install Grafana Server with little tweaks:
--------------------------------------------
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
