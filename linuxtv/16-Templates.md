# USING TEMPLATES WE ARE WORKING WITH THE CONFIGURATION FILES LIKE IN THIS EXAMPLE WE ARE USING SSH SERVICE CONFIGURATION FILE. HERE AWE ARE CUSTOMIZING THE CONFIGURATION FILE OF THE SSH SERVICE BECAUSE SSH IS THE NUMBER 1 WAY THAT HACKERS BREAK INTO THE SERVERS SO TO HAVE A TEMPLATE FILE THAT WE CAN USE TO GO AHEAD AND AUTOMATE OUR CHANGES TO THE SSH SERVICE.

# 1 - Create a 'templates' directory inside base role and create two blank files because ssh config files has different contents for each distributions:

/roles/base/
mkdir templates
cd /roles/base/templates
touch sshd_config_amazon.j2 
touch sshd_config_ubuntu.j2


# NOTE:- LOCATION OF sshd FILE IS SAME ON ALL DISTRIBUTIONS (UBUNTU, DEBIAN AND AMAZON LINUX SERVERS)
/etc/ssh/sshd_config


# 2 - Copy the ssh config files from Amazon Linux and Ubuntu servers into the the RESPECTIVE FILES.
touch sshd_config_amazon.j2 
touch sshd_config_ubuntu.j2



# 3 - Edit both files and add following line:
AllowUsers {{ ssh_users }}


# 4 - Go back few directories and then go to the 'host_vars' directory  and edit all the files.
sudo vim 3.25.71.240.yml

        # Add ssh users and choose the relevant template file:
        ssh_users: "jay simone"
        ssh_template_file: sshd_config_ubuntu.j2

sudo vim 3.25.88.206.yml
        # Add ssh users and choose the relevant template file:
        ssh_users: "jay simone"
        ssh_template_file: sshd_config_amazon.j2
        ssh_service_name: sshd


# 5 - Add another task into the /roles/base/tasks/main.yml

        - name: Generate sshd_config file from template
        tags: ssh
        template:  src="{{ ssh_template_file }}" dest=/etc/ssh/sshd_config owner=root group=root mode=0644
        notify: restart {{ ssh_service_name }}
        ssh_service_name: sshd

# 6 - Create a handlers directory 
cd ..
mkdir handlers
cd handlers
touch main.yml

        # handlers will be indentation same like tasks
        - name: restart sshd
        service: name="{{ ssh_service_name }}" state=restarted