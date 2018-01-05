# Synopsis:
An Ansible template which helps you to create/ delete a defined AWS EC2 Network:

Creation:
 * Create VPC
 * Create DHCP options
 * Create subnets
 * Create VPC ACL
 * Create internet Gateway
 * Create NAT Gateway
 * Create route tables

Deletion:
 * Delete DHCP options
 * Delete NAT Gateway
 * Delete internet Gateways
 * Delete route tables
 * Delete subnets
 * Delete VPC ACL
 * Delete VPC

# Prerequisets:
* Ansible 2.4
* Python 2.7.10
* AWS Account 
* Set following AWS environment variable:
  - AWS_ACCESS_KEY_ID
  - AWS_SECRET_ACCESS_KEY

# Usage:

* Modify variables in 'group_vars/all/main.yam' to own needs.
  - Define aws_region
  - Define company name
  - Define Network Environment example: Test, DEV
  - Define VPC network adress block
  - Define DNS server (optional)
  - define if NAT-Gateway should be created
  - Define subnetname and subnet CIDR
  - Define route tables

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

# TO-DOs:
[TO-DOs](./TODO.md)

# Changelog:
[Changelog](./CHANGELOG.md)

# Contributing:
For any questions use github or email: github@mbloch.de
