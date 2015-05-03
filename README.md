# Create and Provision an EC2 instance with Ansible

This repo is an example of how Ansible can be used to 1. Create EC2 Instances and 2. Provision running EC2 instances.

The aim is to provide very simple template playbooks to show the above mentioned actions.

## Installation

    git clone git@github.com:olluch/ec2-create-provision.git
    cd ec2-create-provision


## Create an EC2 instance

### Configuration
Edit file `roles/launch_instance/vars/main.yml` and set your AWS EC2 preferences that will be used to create the EC2 instance.

Export the following environmental variables:

    export ANSIBLE_HOST_KEY_CHECKING=false
    export AWS_ACCESS_KEY_ID=<your aws access key here>
    export AWS_SECRET_ACCESS_KEY=<your aws secret key here>

### Create a new instance
To create a new EC2 instance named `ec2myserver` run the following command:

    ansible-playbook -i new_hosts create_instance.yml

To change the name of the instance, please append `--extra-vars 'instance_name: newName'` to the above command.

## Provision a running EC2 instance

### Configuration
Edit file `ec2.ini` and set your AWS EC2 preferences that will be used to collect metadata from EC2.

### Provision an instance
Export the following environmental variables:

    export ANSIBLE_HOST_KEY_CHECKING=false
    export AWS_ACCESS_KEY_ID=<your aws access key here>
    export AWS_SECRET_ACCESS_KEY=<your aws secret key here>

To provision a running EC2 instance named `ec2myserver` run the following command:

    ansible-playbook -i ec2.py provision_instances.yml

To provision other machines, please change the hosts variable in `provision_instances.yml` file to match a hosts returned by script `ec2.py`
