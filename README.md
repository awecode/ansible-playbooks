# Ansible Playbooks

## Add user
```bash
ansible-playbook -i inventory/servers.ini user.yaml -e "ansible_user=root" -e "ansible_port=22"
```

If a different user has access, replace `root` with the username.
```bash
ansible-playbook -i inventory/servers.ini user.yaml -e "ansible_user=ecs-user" -e "ansible_port=22"
```

## Harden server
```bash
ansible-playbook -i inventory/servers.ini harden.yaml -e "ansible_port=22" -e "new_port=22222"
```

- SSH port is default `22` until this script is run. So, ansible_port needs to be set to 22 till here.
- But we set new port to `22222` in the environment variable so that the script uses to configure SSH to start using this port now onwards.
- This script also restarts the server after the changes are made. So, please give it a few minutes to boot up.
- Since the port for SSH is changed, please make sure the infrastructure security group and other configurations are updated to use the new port.
- After the script is already run once, you can rerun the playbook without the `ansible_port` environment variables so that it takes the non-default port from the inventory file.
```bash
ansible-playbook -i inventory/servers.ini harden.yaml -e "new_port=22222"
```


## Add deploy key
```bash
ansible-playbook -i inventory/servers.ini deploy_key.yaml
```