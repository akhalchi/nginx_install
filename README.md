You have to prepare your windows host for Ansible using this ps script

https://github.com/ansible/ansible-documentation/blob/devel/examples/scripts/ConfigureRemotingForAnsible.ps1

Generate root CA keys:
ansible-playbook playbooks/generate-ca-root-sert.yml

Encrypt private key using Ansible vault:
ansible-vault encrypt ca_nginx_cert.yml 

Generate keys for server:
ansible-playbook playbooks/generate-server-sert.yml -e "server_name=test.ru days=3365"

Install Nginx:
ansible-playbook playbooks/install-nginx-windows.yml -i inventory.yml



