# Ansible/Vagrant Scripts for Docker cluster

## Prerequisite

* Vagrant
* Ansible (2.1-)


## How to up

First, Execute `vagrant up` for VM Deploy and Provision with ansible.
```
vagrant up
```

Then, create swarm cluster with following commands.

```
[vagrant@mgmt ~]$ docker swarm init  --advertise-addr ${MGMT_IP}:2377
```
```
[vagrant@dc01 ~]$ docker swarm join --token ${TOKEN_GERENATED ABOVE} ${MGMT_IP}:2377
```
```
[vagrant@dc02 ~]$ docker swarm join --token ${TOKEN_GERENATED ABOVE} ${MGMT_IP}:2377
```
```
[vagrant@mgmt ~]$ docker node ls  # To Check
```