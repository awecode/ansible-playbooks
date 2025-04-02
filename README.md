ansible-playbook -i inventory/servers.ini user.yaml -e "ansible_user=root"

ansible-playbook -i inventory/servers.ini harden.yaml

# Add deploy key
ansible-playbook -i inventory/servers.ini deploy_key.yaml