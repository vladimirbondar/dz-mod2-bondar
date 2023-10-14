# dz-mod2-bondar
Template https://github.com/vitabaks/postgresql_cluster

# PREREQUISITES
VMs:

    balancer 10.0.10.2 91.185.84.176 # roles: haproxy. ansible controller
    db1 10.0.10.3 # roles: postgreSQL, patroni
    db2 10.0.10.4 # roles: postgreSQL, patroni
    etcd-srv1 10.0.10.5 # roles: etcd
    etcd-srv2 10.0.10.6 # roles: etcd
    etcd-srv3 10.0.10.7 # roles: etcd

SSH:

    login: vladimir
    ssh_key_public:
        ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDHNHPstSqDdJTy07vs1z/nJb3bva5LeAhiMH0ZWK8suBpuPPKoj4W8wznrSYyTUy5F9yWy7tW9ICBL/olhxw+xTOImiUlCt/ZtVo+0S7h9bhLUYwisS550Rh33OwvVbWRpk2pb3PoOkf0cZ+isLdacgGuwfEqV3P01IoqkoRqTDVUwyLkVH2RbDPRHD64EGTyP6Q/5NM/JnbfTJPyNnRS2PVKFD/YbW5Ub7nc+bYMYBsZToziS6nzYe0SM2SM1ecczzZMTedy1lagZX+OAH7K9Xlp7zfwt60TPa6QAZk11Ln+b+acsNqNXC0QLWxGyksPgTgwrmXoo9O8FArj4S0mMzJhN6aUb+FnXcoer1FuV+MwG2JxXOqhEoaxEYrU9Olhkw8Oidir 2CPH+JPI4JPpqmLhhQM2vE+ruK2XqrLH30s1fj+tHUbNCY0TDP5tkJwQG9DB6X96hTU5LSobnjHZ9zu3LlCj7HHNCJ1Xw+VZXuwfTOH/Ouq3IyHrdfACpeyLQM= vladimir@mbp--bond
    ssh_key_file: /home/bond/.ssh/bond.key # proivided separately

INSTALLATION:

    sudo apt update
    sudo apt install -y python3-pip
    pip install ansible
    git clone https://github.com/vladimirbondar/dz-mod2-bondar.git
    cd dz-mod2-bondar/ansible
    ansible -i inventory -m ping all
    ansible-playbook -i inventory deploy_pgcluster.yml

CHECK:

    http://<balancer public address>:7000
    PSQL: address=<balancer public address> port=5000 username=postgres password=postgress-pass
