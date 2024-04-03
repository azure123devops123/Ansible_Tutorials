# @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@ UBUNTU SERVER - 1 @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@ #
# 1 - Ubuntu Server - Create a user and add to sudo group for sudo access.
sudo adduser jay
sudo cat /etc/passwd
sudo cat /etc/group
sudo usermod -a -G sudo jay

# 2 - Set the host name
sudo hostnamectl set-hostname ubuntu
sudo /bin/bash

# 3 - Enable Password Authentication and then restart service.
sudo vim /etc/ssh/sshd_config
     -> Disable the inheritance within /etc/ssh/sshd_config # Include /etc/ssh/sshd_config.d/*.conf and set PasswordAuthentication yes
sudo service sshd restart


# @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@ AMAZON LINUX SERVER - 2 @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@ #
# 1 - Amazon Linux Server - Create a user and add to wheel group for sudo access.
sudo useradd jay
passwd jay
sudo usermod -aG wheel jay

# 2 - Set the host name
sudo hostnamectl set-hostname amazon-linux
sudo /bin/bash

# 3 - Enable Password Authentication and then restart service:
sudo vim /etc/ssh/sshd_config
     -> PasswordAuthentication yes   #  CHANGE from no to yes 
sudo service sshd restart


# @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@ CONTROL HOST - OUR LAPTOP @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@ #
# Generate a key pair on workstation and copy the public key to a remote targeted host:
ssh-keygen -t ed25519 -C "ansible"           # /Users/muhammadjabir/.ssh/ansible
ls -la /Users/muhammadjabir/.ssh             # notice:- ansible.pub PUBLIC KEY and ansible PRIVATE KEY

ssh-copy-id -i /Users/muhammadjabir/.ssh/ansible.pub jay@3.105.229.9        # amazon linux server     
ssh-copy-id -i /Users/muhammadjabir/.ssh/ansible.pub jay@13.210.80.25       # ubuntu server 


# @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@ CHECKING THE COPIED KEY ON BOTH REMOTE SERVERS @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@ #
Now login to the remote hosts one by one and check the .ssh/authorized_keys file. You will see an entry of the public key which we copy above.


# @@@@@@@@@ DISABLE THE PASSWORD AUTHENTICATION ON BOTH REMOTE SERVERS BECAUSE KEY AUTHENTICATION IS MORE SAFE RATHER THEN PASSWORD AUTHENTICATION @@@@@@@ #
# ON UBUNTU SERVER: Disable Password Authentication and then restart service.
sudo vim /etc/ssh/sshd_config
     -> Enable the inheritance within /etc/ssh/sshd_config       Include /etc/ssh/sshd_config.d/*.conf and set PasswordAuthentication no
sudo service sshd restart


# ON AMAZON LINUX SERVER: Disable Password Authentication and then restart service.
sudo vim /etc/ssh/sshd_config
     -> PasswordAuthentication no   #  CHANGE from yes to no 
sudo service sshd restart


