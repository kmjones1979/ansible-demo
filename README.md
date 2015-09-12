# Ansible / NGINX Plus Demo

This is a demonstration on how to deploy and configure NGINX Plus as both a load
balancer and a webserver on CentOS7 using Ansible.

Tested using...

```
[kjones@zion-development ~]$ cat /etc/redhat-release 
CentOS Linux release 7.1.1503 (Core)

[kjones@zion-development ~]$ ansible --version
ansible 1.9.2
```

#### Checkout ansible-demo

```
git clone git@github.com:kmjones1979/ansible-demo.git
```

#### Install Ansible

```
sudo yum install -y epel-release
sudo yum update
sudo yum install -y ansible
```

#### Configure Ansible hosts file
```
sudo vim /etc/ansible/hosts
```

This repository contains two ansible deployment configurations for 
both NGINX Plus as a load balancer and NGINX Plus as a webserver

Example Ansible hosts file...

```
# /etc/ansible/hosts

[nginxplus-lb]
nginxplus-lb1.domain.com
[nginxplus-ws]
nginxplus-ws1.domain.com
nginxplus-ws2.domain.com
nginxplus-ws3.domain.com
```

#### Setup authorization over SSH

From your ansible server generate an ssh-key for your root account...

```
su -c 'ssh-keygen'
sudo cat /root/.ssh/id_rsa.pub
```

...and copy the ssh key to your destination servers 'authorized_keys' file
that you defined in the ansible hosts file.

```
sudo vim /root/.ssh/authorized_keys
```

#### Deploy

```
ansible-playbook 
```
