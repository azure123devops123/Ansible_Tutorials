# What are the benefits of Jinja 2 Templates:
1) Dynamic Configuration
2) Dynamic Script

# Important Steps while using Jina 2 template:
1) File Extension must be j2: any_file_name.j2
2) Interpolation Syntax - define in the custom configuration file for dynamic value: {{ server_port }}
3) Call the Jinja 2 template using 'template' module. Provide full source path of Jinja 2 file and full destination path
4) Define the value by using 'vars' module at the task level or playbook level.