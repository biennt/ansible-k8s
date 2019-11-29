# ansible-k8s
Installing a k8s cluster by ansible playbook

1. Install ansible into ansible host (tested with Centos7)
```
sudo yum install ansible
```
Clone this repo to your Ansible host:
```
git clone https://github.com/biennt/ansible-k8s.git
```

2. Edit hosts and env_variables<br>
In the hosts file, masters is the master node. nodes is the worker nodes. IP addresses here should be reachable by Ansible host
```
[masters]
18.163.100.11

[nodes]
18.163.114.21
18.162.113.193
```
In the env_variables file, ad_addr is the ip address of the master node which reachable by worker nodes (private address)
```
# ad_addr is master server, which other nodes/clients to connect to
ad_addr: 172.31.1.153
cidr_v: 172.16.0.0/16

packages:
- kubeadm
- kubectl

services:
- docker
- kubelet

token_file: join_token
```
