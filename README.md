#Synopsis:
An Ansible template which helps you to create/ delete a defined AWS EC2 Network:
* Create VPC
* Create DHCP options
* Create Subnets
* Create VPC ACL
* Create Internet Gateway
* Create NAT Gateway

#Prerequisets:
* Ansible 2.4
* Python 2.7.10
* AWS Account and configured Access Key and Secret Access Key
* EC2.PY & EC2.INI are configured and loaded ( see https://github.com/ansible/ansible/tree/devel/contrib/inventory )
* Set following AWS environment variable:
  - AWS_ACCESS_KEY_ID
  - AWS_SECRET_ACCESS_KEY

#Usage:

* Modify variables in 'group_vars/all/main.yam' to own needs.
  - Define aws_region
  - Define company name
  - Define Network Environment example: Test, DEV
  - Define VPC Network Adress block
  - Define DNS Server
  - Define Subnetname and Subnet CIDR

To create a network:
```
# ansible-playbook aws_create_network.yml
```
To delete a network:
```
# ansible-playbook aws_delete_network.yml
```

The network will be created with following VPC ACL rules:
Incoming: 
* Allow Port 22 & 80
* Allow Ping requests
Outgoing:
* Allow everything

They can be modified in following file: **roles/aws_create_network/tasks/create_vpc_acl.yml**

#TO-DOs:
[TO-DOs](./TO-DO.md)

#Changelog:
[Changelog](./CHANGELOG.MD)

#Contributing:
For any questions use github or email: github@mbloch.de
