# dz-mod2-bondar

## PREREQUISITES
VMs:
    node1 10.0.10.2 # roles: ansible, haproxy
    node1 10.0.10.3 # roles: postgreSQL, patroni
    node1 10.0.10.4 # roles: postgreSQL, patroni, etcd
    node1 10.0.10.5 # roles: etcd
    node1 10.0.10.6 # roles: etcd

    login: bond
    ssh_key_public:
        ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDHNHPstSqDdJTy07vs1z/nJb3bva5LeAhiMH0ZWK8suBpuPPKoj4W8wznrSYyTUy5F9yWy7tW9ICBL/olhxw+xTOImiUlCt/ZtVo+0S7h9bhLUYwisS550Rh33OwvVbWRpk2pb3PoOkf0cZ+isLdacgGuwfEqV3P01IoqkoRqTDVUwyLkVH2RbDPRHD64EGTyP6Q/5NM/JnbfTJPyNnRS2PVKFD/YbW5Ub7nc+bYMYBsZToziS6nzYe0SM2SM1ecczzZMTedy1lagZX+OAH7K9Xlp7zfwt60TPa6QAZk11Ln+b+acsNqNXC0QLWxGyksPgTgwrmXoo9O8FArj4S0mMzJhN6aUb+FnXcoer1FuV+MwG2JxXOqhEoaxEYrU9Olhkw8Oidir 2CPH+JPI4JPpqmLhhQM2vE+ruK2XqrLH30s1fj+tHUbNCY0TDP5tkJwQG9DB6X96hTU5LSobnjHZ9zu3LlCj7HHNCJ1Xw+VZXuwfTOH/Ouq3IyHrdfACpeyLQM= vladimir@mbp--bond
    ssh_key_file: /home/bond/.ssh/bond.key # to be proivided separately

## Deployment: quick start
0. [Install Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html) on one control node (node1)

```
sudo apt update && sudo apt install -y python3-pip git
pip3 install ansible
```

1. Download or clone this repository
```
git clone https://github.com/vladimirbondar/dz-mod2-bondar.git
```
2. Go to the playbook directory
```
cd postgresql_cluster/
```
3. Try to connect to hosts
```
ansible all -m ping
```
4. Run playbook:
```
ansible-playbook deploy_pgcluster.yml
```