# 0 - Youtube link: https://www.youtube.com/watch?v=C5mazUJ1dsg


# 1 - MUST INSTALL:
python3 --version
pip3 --version 
pip show boto3                  # we need pip to install boto3 aws sdk.    inst pip instal boto3
ansible --version


# 2 - WHY DYNAMIC INVENTORY SOLUTION: EC2 instances's ip addresses always keep changes due to AUTOSCALING.
https://docs.ansible.com/ansible/latest/collections/amazon/aws/aws_ec2_inventory.html
vim inventory/01_aws_ec2.yml            # aws_ec2.yml must be at the end. It acts like a dynamic inventory file


# 3 - TWO WAYS TO CONFIGURE CREDENTIALS:
(1) IF WE ARE RUNNING CONTROL MACHINE ON AWS CLOUD THEN CREATE IAM ROLE AND ATTACH TO CONTROL MACHINE EC2 INSTANCE.
(2) IF WE ARE RUNNING CONTROL MACHINE LOCAL LAPTOP THEN CREATE IAM USER AND GET ACCESS KEYS AND SECRET KEYS.      # aws configure


# 4 - LIST DOWN THE EC2 INSTANCES USING DYNAMIC INVENTORY FILE.
ansible-inventory -i inventory/01_aws_ec2.yml --list               // get all the ec2 instances in the region we defined in 01_aws_ec2.yml
OR
ansible-inventory aws_ec2 -i inventory/01_aws_ec2.yml --list      // get all the ec2 instances in the region we defined in 01_aws_ec2.yml
Note:- In the above command 'aws_ec2' is the group name.


# 5 - To manage the hosts we need private keys (*.pem) download on control node and make sure to change permissions to 400 permissions on .pem file
# RUN 'ping' AD HOC COMMAND ON GROUP (aws_ec2) OF EC2 INSTANCES:
ansible aws_ec2 -i inventory/01_aws_ec2.yml --private-key=~/aws/aws_keys/jabir-practice.pem -m ping
# INSTALL GIT USING AD HOC COMMAND:
ansible aws_ec2 -i inventory/01_aws_ec2.yml --private-key=~/aws/aws_keys/jabir-practice.pem -m yum -a 'name=git state=present' --become    


# 6 - Create a configuration file 'ansible.cfg' 
ansible aws_ec2 -m ping
ansible aws_ec2 -m yum -a 'name=git state=present' --become

