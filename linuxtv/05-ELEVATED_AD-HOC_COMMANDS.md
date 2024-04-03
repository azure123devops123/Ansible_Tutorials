# Update Cache Index
ansible all -m package -a update_cache=true --become --ask-become-pass   # provide sudo password - it will only work if we have same sudo password on all hosts

# Upgrade - it will only work on ubuntu but not on amazon linux
ansible all -m package -a 'upgrade=dist' --become --ask-become-pass

# Install git, tmux packages on all servers
ansible all -m package -a 'name=git state=present' --become --ask-become-pass
ansible all -m package -a 'name=tmux state=present' --become --ask-become-pass

# We can check the log to verify