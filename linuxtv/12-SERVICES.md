# make sure add the tags to the services
# we can manually stop the services and can start using service module via playbook.
# On Amazon Linux Server: test case is change email address using 'lineinfile' module in the following config file
 1) make a change into a config file    '/etc/httpd/conf/httpd.conf'
    search: / e-mail
    add line numbers for more visibility: :set number
    we want to make changes to line 91 ServerAdmin root@localhost

 2) restart the service so changes can be reflected.
 3) vim /etc/httpd/conf/httpd.conf +91    // check line 91
    OR
    cat /etc/httpd/conf/httpd.conf | grep ServerAdmin
    systemctl status httpd     // check the time since the service is running to see if actually it restarted or not

4) Immediately, re-run the playbook to MAKE SURE THERE ARE NO CHANGES THIS TIME because we did not make any changes. Import because when we are working with the config files and using 'fileinline' module if we have any typos or any problem it will duplicate the line. so we have to be careful. its very common problem.
   ansible-playbook playbooks/05-site-manage-services.yml --tags "httpd" --ask-become-pass

# On Ubuntu Server:  
1) make a change into a config file      '/etc/apache2/sites-available/000-default.conf'
rest the similar stuff.