#Readme
In this series we will be installing ansible and connecting to our vCenter Server and clone a template.
We will then use these templates to setup a docker swarm cluster with a shared glusterfs backend for storage.
Basically automating everything we did manually in the previous videos.

### Requirements
- Vsphere template with Ubuntu 18.04
- add a user in the template that will run ansible (ansible) -> use adduser
- set a password on the account
- set the account for password-less sudo -> visudo
- copy the cleanup script to your template VM and run it, to fix the vsphere/ubuntu 18.04  template bug: [here](https://kb.vmware.com/s/article/54986)

***If you need help doing the above drop me a comment***

###install Prerequirements

sudo apt install python3-pip -y

sudo pip3 install ansible

ansible --version

``ansible 2.9.6
  config file = None
  configured module search path = ['/home/piwi/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/local/lib/python3.6/dist-packages/ansible
  executable location = /usr/local/bin/ansible
  python version = 3.6.9 (default, Nov  7 2019, 10:44:02) [GCC 8.3.0]``

### ssh keys

Ansible uses ssh and ssh keys to authenticate and connect to all the machines that we will be deploying
lets generate a ssh key for our local user

```ssh-keygen -t rsa```

### Prepare your ansible runner
We now run our ansible-runner preparation playbook

(make sure you are in the code directory)
````
ansible-playbooks playbooks/prepare.yml
````

