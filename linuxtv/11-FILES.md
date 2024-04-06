# create an HTML file as a source code - make sure that 'files' directory must be be located inside the playbooks 
mkdir files
cd files
vim default_site.html

# files directory must be located with all the playbooks.
ls /Users/muhammadjabir/Desktop/my_ansible/Ansible_Tutorials/playbooks
➜  playbooks git:(main) ✗ ls
01-ping.yml           02-remove-apache.yml  03-site.yml           files
02-install-apache.yml 03-site-tags.yml      04-site-files.yml


# copy the source code to the web servers and check it
ls /var/www/html/

