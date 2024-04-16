# Cleaner Directories:
mkdir -p roles/web_servers/tasks
mkdir -p roles/db_servers/tasks
mkdir -p roles/file_servers/tasks
mkdir -p roles/control_host/tasks
mkdir -p roles/base/tasks



# CREATE main.yml files
cd roles/web_servers/tasks
touch main.yml
cd ../../../

cd roles/db_servers/tasks
touch main.yml
cd ../../../

cd roles/file_servers/tasks
touch main.yml
cd ../../../

cd roles/control_host/tasks
touch main.yml
cd ../../../

cd roles/base/tasks
touch main.yml
cd ../../../



# TREE STRUCTURE 
➜  14-ROLES git:(main) ✗ tree          
.
└── roles
    ├── base
    │   └── tasks
    │       └── main.yml
    ├── control_host
    │   └── tasks
    │       └── main.yml
    ├── db_servers
    │   └── tasks
    │       └── main.yml
    ├── file_servers
    │   └── tasks
    │       └── main.yml
    └── web_servers
        └── tasks
            └── main.yml

12 directories, 5 files


# COPY THE files DIRECTORY
cp -R ../files/ ../14-ROLES/roles/web_servers