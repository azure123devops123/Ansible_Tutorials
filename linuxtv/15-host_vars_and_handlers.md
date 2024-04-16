# Create a directory at the root level where site.yml is present.

mkdir host_vars
cd host_vars
touch 52.65.133.171.yml             # Note:- It could be ip_address.yml OR dns_name.yml OR hostname.yml

            # Packages Names:
            apache_package_name: httpd
            php_package_name: php


            # Services Names:
            apache_service_name: httpd

touch 54.66.200.219.yml
            # Packages Names:
            apache_package_name: apache2
            php_package_name: libapache2-mod-php


            # Services Names:
            apache_service_name: apache2

# call these variables inside the main.yml in the web_servers directory.

# Run the playbook and you will notice no change.

--------- HANDLERS -----------

# Create a handlers directory at the tasks level.

mkdir handlers
cd handlers
touch mail.yml

        # handlers will be indentation same like tasks
        # ---
        # handlers:
        - name: restart httpd
        service: name="{{ apache_service_name }}" state=restarted

        - name: restart apache2
        service: name=" {{ apache_service_name }}" state=restarted