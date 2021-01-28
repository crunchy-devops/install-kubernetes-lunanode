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