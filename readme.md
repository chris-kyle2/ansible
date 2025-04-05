## Ansible Roles
ansible-galaxy install -p /home/bob/playbooks/roles geerlingguy.nodejs

### Create a role
ansible-galaxy init /home/bob/playbooks/roles/package



### Install a role
ansible-galaxy install -p /home/bob/playbooks/roles geerlingguy.nodejs

### Install a collection
ansible-galaxy collection install community.general
