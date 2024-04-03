# INSTALLATION:
python3 --version
pip3 --version 
pip show boto3                  # we need pip to install boto3 aws sdk.    inst pip instal boto3
ansible --version


# ADHOC COMMANDS:
ansible-inventory -i ansible_hosts --list   OR   ansible-inventory --list
ansible-inventory -i ansible_hosts --graph  OR   ansible-inventory --graph
ansible all --list-hosts

ansible all -m ping
ansible all -m gather_facts
ansible all -m gather_facts --limit 13.211.56.161               // Against a particular host

