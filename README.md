# Nginx Installation and Configuration with Ansible on Windows

This repository contains Ansible playbooks for setting up and configuring Nginx on a Windows host. Follow the steps below to prepare your environment and execute the playbooks.

## Preparation


### Allow sudo on Linux localhost
```sh
sudo visudo
```
add string "your_username ALL=(ALL) NOPASSWD:ALL"

and save

### Configure Windows Host for Ansible

Run the following PowerShell script on your Windows host to configure WinRM for Ansible:

[ConfigureRemotingForAnsible.ps1](https://github.com/ansible/ansible-documentation/blob/devel/examples/scripts/ConfigureRemotingForAnsible.ps1)

```powershell
. .\ConfigureRemotingForAnsible.ps1
```

### Install Ansible on localhost
Manual for [your OS](https://docs.ansible.com/ansible/latest/installation_guide/installation_distros.html).

It was tested for Ansible 2.15.12

### Download project
In your home directory
```sh
git clone --depth=1  https://github.com/akhalchi/nginx_install.git
```
### Install collections
```sh
cd nginx_install/

ansible-galaxy collection install -r requirements.yml --force
```

## Run
```sh
ansible-playbook playbooks/main.yml -i inventories/inventory.yml -e "server_name=test.ru days=365" --ask-vault-pass
```
type "vaultpassword"


