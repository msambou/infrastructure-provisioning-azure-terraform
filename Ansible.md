
## Ansible

### Install Ansible

    # Update packages
    sudo apt update

    # Install ansible
    sudo apt install ansible -y


### Setting Up the Inventory File
The inventory file contains information about the hosts you’ll manage with Ansible. You can include anywhere from one to several hundred servers in your inventory file, and hosts can be organized into groups and subgroups. 

    sudo nano /etc/ansible/hosts

Add the following code sections to the end of the file

    [webservers]
    server1 ansible_host=<server-ip-address-from-terraform>
    server1 ansible_ssh_private_key_file=<path-to-your-key-file>

    [all:vars]
    ansible_python_interpreter=/usr/bin/python3

Whenever you want to check your inventory, you can run:

    ansible-inventory --list -y


### Pinging the Server

    ansible all -m ping -u azureuser


## Ansible Playbook

    cd ~
    mkdir playbooks
    cd playbooks

    # Create a simple web site to display welcome to the DevOps class!
    echo "Welcome to the DevOps Class!" > index.html

    # Create ansible playbook to install apache web server.
    nano install-apache.yaml

### Ansible playbook contents

    - name: Ansible Playbook to Install and Setup Apache on Ubuntu
      hosts: webservers
      become: yes
      tasks:
        - name: Install latest version of Apache
          apt: name=apache2 update_cache=yes state=latest

        - name: Replace the content of index.html
          become: yes
          copy:
             src: ~/playbooks/index.html
             dest: /var/www/html


Save the file
CTRL + O

Exit the editor
CTRL + X

### Run the playbook

    ansible-playbook install-apache.yaml 





