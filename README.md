# Nginx Installation and Configuration with Ansible on Windows

This repository contains Ansible playbooks for setting up and configuring Nginx on a Windows host. Follow the steps below to prepare your environment and execute the playbooks.

## Prerequisites

1. Ensure you have Ansible installed on your control machine.
2. Prepare your Windows host for Ansible by configuring WinRM.

## Preparation

### Configure Windows Host for Ansible

Run the following PowerShell script on your Windows host to configure WinRM for Ansible:

[ConfigureRemotingForAnsible.ps1](https://github.com/ansible/ansible-documentation/blob/devel/examples/scripts/ConfigureRemotingForAnsible.ps1)

```powershell
. .\ConfigureRemotingForAnsible.ps1
```

## Install

## Generate Root CA Keys

Generate the root CA keys by running the following playbook:
```sh
ansible-playbook playbooks/generate-ca-root-cert.yml
```

## Encrypt Private Key
Encrypt the private key for security purposes using Ansible Vault:
```sh
ansible-vault encrypt ca_nginx_cert.yml
```

# Generate Keys for Server
Generate the necessary keys for your server by running the playbook and specifying the server name and the number of days the certificate should be valid:
```sh
ansible-playbook playbooks/generate-server-cert.yml -e "server_name=test.ru days=3365"
```
# Install Nginx
Finally, install and configure Nginx on your Windows host using the following playbook:
```sh
ansible-playbook playbooks/install-nginx-windows.yml -i inventories/inventory.yml
```