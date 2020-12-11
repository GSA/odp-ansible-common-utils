# odp-ansible-common-utils
It's an ansible role that installs utility software that have to be prebaked in Amazon Machine Image (AMI)

### Install
Following list of software is installed by this role
* python3-pip
* collectd
* CloudWatch agent

### Configure
In addition to the installation, it also configures the the CloudWatch agent with the following default parameters:

```
cw_metrics_collection_interval: 60
cw_metrics_aggregation_interval: 60
```

### OS Support
It supports the following Linux Operating systems:
* Ubuntu
* RedHat
* CentOS
* Amazon

### How to execute this role?
* Create a Inventory File. For example ~/inventory file:
```
[machines]
your-redhat-machine ansible_user=ec2-user ansible_ssh_private_key_file=your-ssh-key-file-path 
your-centos-machine ansible_user=centos ansible_ssh_private_key_file=your-ssh-key-file-path 
your-ubuntu-machine ansible_user=ubuntu ansible_ssh_private_key_file=your-ssh-key-file-path 
your-amazon-machine ansible_user=ec2-user ansible_ssh_private_key_file=your-ssh-key-file-path 
```

* Create a playbook. For example ~/playbook.yml file:
```
- hosts: all
  roles:
    - odp-ansible-common-utils
```

* Execute the playbook as given below to run on all the hosts:

```
ansible-playbook -i ~/inventory ~/playbook.yml
```






