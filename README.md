## Steps to install and configue loadbalancer on AWS using Ansible

**Prerequisites:**
* IAM User with the required permission
* Boto installed (Ansible uses the Boto Python library to handle AWS management)
* haproxy installed and configured for providing the configuration of loadbalancer instance 

#### Load Balancer:
In this scenerio we shall launch 5 instances on AWS named 
* ‘ansibleweb’, four instances, which serves as the webservers on the backend
* ‘load-balancer’ one instance, which is configured as the front end load balancer

#### Command to run the playbook for creating the instances
```
ansible-playbook --ask-vault-pass instancelaunch.yml 
```
#### Retrieve the IPs of these instances dynamically
To do this, we will be using files ec2.py and ec2.ini which are downloaded in a folder named dynamic_inventory which serves as the inventory for our ansible configuration file.
These two downloaded files are then made executable.
> wget https://raw.githubusercontent.com/ansible/ansible/stable-2.9/contrib/inventory/ec2.py
> wget https://raw.githubusercontent.com/ansible/ansible/stable-2.9/contrib/inventory/ec2.ini
**Note:** In the ec2.py file edit the first line as #!/usr/bin/python3

#### Retrive the IP address for all the deployed hosts using the command
```
ansible all --list-hosts
```
#### Command to run the playbook for launching the instances
```
ansible-playbook --ask-vault-pass instancelaunch.yml 
```