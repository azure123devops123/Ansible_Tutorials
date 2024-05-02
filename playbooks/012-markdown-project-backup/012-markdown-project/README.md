# Ansible Website Deployment:
Local System: ssh-key -> private and public -> copy pub to hosting server for connection
Local System: Markdown -> HUGO GO FRAMEWORK static site generator  -> html -> zip -> to remote server
Remote Server: unzip -> html
Remote Server: cache clear

# Commands:
hugo
hugo serve


1) one playbook to copy the ssh key to remote server.
2) 