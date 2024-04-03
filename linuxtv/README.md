# Git setting up username and email address:
➜ git config --global user.name "azure123devops123"    
➜ git config --global user.email "azure123.devops123@gmail.com"
➜ cat ~/.gitconfig 

# Create a new repository on the command line
➜ echo "# Ansible_Tutorials" >> README.md
➜ git init
➜ git add README.md
➜ git commit -m "first commit"
➜ git branch -M main
➜ git remote add origin https://github.com/azure123devops123/Ansible_Tutorials.git
➜ git push -u origin main



