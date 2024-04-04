# We added some tags on task level.
# Tags are meta-data 
# After adding tags when we run our playbook nothing will change 
# Tag will help us to target specific hosts while testing rather then running the whole playbook.

# list all tags
ansible-playbook playbooks/03-site-tags.yml --list-tags         

# targeting a specific tag
ansible-playbook playbooks/03-site-tags.yml --tags ubuntu --ask-become-pass
ansible-playbook playbooks/03-site-tags.yml --tags samba --ask-become-pass
ansible-playbook playbooks/03-site-tags.yml --tags amazon --ask-become-pass

# targeting multiple tags
ansible-playbook playbooks/03-site-tags.yml --tags "amazon,samba" --ask-become-pass