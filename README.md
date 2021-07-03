# ansible-swarm-clowder
This repository does the following things:
* create a HEAT stack
* install neccessary tools/libraries
* deploy a swarm cluster
* deploy Clowder in that swarm cluster
All is done via a Makefile


Thanks to Zane for his work on Makefile and templates ...


# Deployment steps

## Requirements

* You need to have openstack 5.2.0 installed (apt install python3-openstackclient)
* Download the Openstack RC file
* Ansible version 2.9 
* Make installed, in ubuntu: sudo apt-get install build-essential
* Create vars/secrets.yml based on vars/secrets.yml.example

## Create HEAT stack for Docker Swarm

* edit setupenv-openstack. Make sure you get the IMAGE_ID and OS_PROJECT_NAME right.The IMAGE_ID should be a Ubuntu image.  

* make stack
* Create a DNS that points to the first master node, this DNS should match clowder_host field in vars/secrets.yml

## Deploy Docker swarm

* make init-swarm
* To inspect swarm cluster: make inspect-swarm

## Deploy Clowder in swarm

* make deploy-clowder

## Destroy Clowder in swarm

* make destroy-clowder

## Destroy swarm cluster

* make destroy-swarm

## Delete stack

* make destroy-stack


