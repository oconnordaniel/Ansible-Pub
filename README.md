# Ansible

This playbook is used to setup a base setup for my homelab servers

## Setup python and ansible

``` bash
sudo {{ package manager }} install python3 python3-pip python3-venv
python3 -m venv ans-venv
source ans-venv/bin/activate
python3 -m ensurepip --default-pip
python3 -m pip install ansible
```

## Gen SSH keys to be used

``` bash
ssh-keygen -t ed_25519 -C ansible-key -f ./files/id_ed25519_ansible
cat ./files/id_ed25519_ansible.pub >> plays/roles/ssh/files/authorized_keys 
```

You should also cat your .pub keys for whatever users / computers you want into this authorized_keys file. Here I manage what computers are allowed to log into any of my computers. The ssh role will disable password ssh login for security. I also put the .pub key in the cloudinit file for my ubuntu server templates.

