# ansible-k8s
Install a k8s cluster by ansible playbooks<br>
- tested with Centos7 for ansible host, k8s master and worker nodes)
- Assuming that user on ansible host and k8s nodes are centos, authenticate by SSH Key (no password)

1. Install ansible into ansible host
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
....
```
3. Run the playbooks
Download, install packages
```
ansible-playbook --private-key your_private_key.pem setting_up_nodes.yml
```
Configure the master node
```
ansible-playbook --private-key your_private_key.pem configure_master_node.yml
```
Configure the worker nodes
```
ansible-playbook --private-key your_private_key.pem configure_master_node.yml
```
Enjoy!
