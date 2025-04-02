ansible-playbook -i inventory/servers.ini user.yaml -e "ansible_user=root" -e "ansible_port=22"

ansible-playbook -i inventory/servers.ini harden.yaml

# Add deploy key
ansible-playbook -i inventory/servers.ini deploy_key.yaml