# Install-kubernetes-lunanode 
## Pre-requis pour ubuntu
```shell
sudo apt-get update
sudo apt-get install -y git wget 
sudo apt-get install -y htop iotop iftop
sudo apt-get install -y python3 python3-venv
sudo apt-get install -y sshpass
```
## Installation d'un virtualenv Python 
```shell
git clone https://github.com/crunchy-devops/install-kubernetes-lunanode.git
cd install-kubernetes-lunanode
python3 -m venv venv
source venv/bin/activate
pip3 install wheel
pip3 install ansible
ansible --version
```
## Create an inventory file 
```ini
[master]
164.132.212.121 ansible_ssh_user=ubuntu  ansible_ssh_pass=xxxx ansible_ssh_extra_args='-o StrictHostKeyChecking=no'
[node]
51.255.211.165 ansible_ssh_user=ubuntu  ansible_ssh_pass=xxx ansible_ssh_extra_args='-o StrictHostKeyChecking=no'
```

## Install Kubernetes
```shell
ansible-playbook -i inventory playbook.yml
```