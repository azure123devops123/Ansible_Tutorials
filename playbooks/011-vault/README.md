###### OPTION 1. CREATE A ENCRYPTED FILE USING PASSWORD ######

# CREATE ENCRYPTED FILE USING ANSIBLE VAULT:
ansible-vault create my_vault_with_password.yml

# EXTRA OTHER OPTIONS: - ( DID NOT KNOW HOW TO SET THE PASSWORD FOR THE VAULT )
vim plain_text_secret_file.yml
ansible-vault encrypt plain_text_secret_file.yml
ansible-vault decrypt plain_text_secret_file.yml


# VIEW ENCRYPTED FILE USING ANSIBLE VAULT:
cat my_vault_with_password.yml                        # Can not view the actual contents
ansible-vault view my_vault_with_password.yml         # Can view the actual contents

# CHANGE THE CONTENTS OF ENCRYPTED FILE USING ANSIBLE VAULT:
ansible-vault edit my_vault_with_password.yml

# CHANGE THE PASSWORD:
ansible-vault rekey my_vault_with_password.yml

# RUN THE PLAYBOOK WITH THE --ask-vault-pass OPTION AND VIEW THE CONTENTS OF THE ENCRYPTED FILE my_vault_with_password.yml
ansible-playbook playbooks/011-vault/my_vault_show.yml -e @playbooks/011-vault/my_vault_with_password.yml --ask-vault-pass





###### OPTION 2. CREATE AN ENCRYPTED FILE BY USING PASSWORD FILE ######

# GENERATE A BASE64 PASSWORD FILE:
mkdir pass_file
cd pass_file
touch ansible-vault.pass
cd ..
openssl rand -base64 2048 > pass_file/ansible-vault.pass            # Generate a random strong password and save it into the above created file

# CREATE A NEW ENCRYPTED FILE BY USING THE PASSWORD FILE:
ansible-vault create my_vault_with_base64_password_file.yml --vault-password-file=pass_file/ansible-vault.pass

# VIEW THE CONTENTS OF THE ENCRYPTED FILE BY USING THE PASSWORD FILE:
ansible-vault view my_vault_with_base64_password_file.yml --vault-password-file=pass_file/ansible-vault.pass

# RUN THE PLAYBOOK WITH THE --vault-password-file OPTION AND VIEW THE CONTENTS OF THE ENCRYPTED FILE my_vault_with_base64_password_file.yml
ansible-playbook playbooks/011-vault/my_vault_show.yml -e @playbooks/011-vault/my_vault_with_base64_password_file.yml --vault-password-file=playbooks/011-vault/pass_file/ansible-vault.pass




###### OPTION 3. READING THE ANSIBLE PASSWORD FILE FROM ENVIRONMENT VARIABLE - ANSIBLE_VAULT_PASSWORD_FILE ######

# EXPORT THE FULL PATH OF THE BASE64 PASSWORD FILE:
export ANSIBLE_VAULT_PASSWORD_FILE=/Users/muhammadjabir/Desktop/my_ansible/Ansible_Tutorials/playbooks/011-vault/pass_file/ansible-vault.pass
echo $ANSIBLE_VAULT_PASSWORD_FILE

# NOW WE DO NOT NEED TO PASS THE BASE64 PASSWORD FILE PATH BECAUSE WE EXPORTED THE PATH IN AN ENVIRONMENT VARIABLE: (IMPORTANT: ITS ONLY TERMINAL SESSION BASED)
ansible-playbook playbooks/011-vault/my_vault_show.yml -e @playbooks/011-vault/my_vault_with_base64_password_file.yml