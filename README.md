Role Name
=========

A Ansible role to configure Kubernetes multinode cluster on AWS.

Requirements
------------

Have atleast 3 EC-2 instances launched, So as to configure them as master and two slaves. Any number of slaves can be used. Use only Amazon Linux AMI to create the instances.The user that ansible is using to login to instances should be a IAM PowerUser.

the master ip should be under `kube_master` group and the slave nodes under `kube_workers`. So make inventory accordingly

Run this command 

```
chmod 400 <path-of-key-file>
```

Role Variables
--------------

podcidr is the variable for pod-network-cidr

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

create the setup.yml file like-

```
- hosts: all
  roles:
  - role: "<path-of-role-folder>"

```

create the ansible.cfg file like-

```
[defaults]
host_key_checking = False
roles = <path-of-role-folder>
inventory = <path-of-inventory-file>
ask_pass = False
remote_user = ec2-user
private_key_file = <path-of-key-file>
[privilege_escalation]
become = True
become_method = sudo
become_user = root
become_ask_pass = False
```

set the roles path with the following -

```
ansible-playbook <path-of-setup.yml> --roles-path <path-of-role-folder>
```

Author Information
------------------

Yash Indane
Email: yashindane46@gmail.com
