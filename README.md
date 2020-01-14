# Ansible
Getting Started with Ansible

Create your Instances on AWS 
One Instance should be the Master, and others slaves/nodes

Installation on Master

sudo apt update

sudo apt-add-repository ppa:ansible/ansible

sudo apt install ansible

sudo apt update

Installation on slaves/nodes

sudo apt-get install python

goto Master, and try to connect to a slave/node like so:

cd .ssh

ssh ubuntu@'ip address of slave/node'

Denied!!!

Create key on Master and give permission like so:

ssh-keygen

'ls' to see files

you would see authorized key rsa rsa_pub

cat id_rsa.pub to see the public key

copy the public key

goto slave/nodes

cd .ssh

'ls' to see files

you would see authorized keys

sudo vim .ssh/authorized_keys

'dd' to remove authorized key

Paste copied public key from Master

:wq! to save and exit

goto master

ssh ubuntu@'ip address of slaves/hosts' to connect to slave servers.

Configure the host files

 this lets us host files, create staging, run command without going into server.
 
 sudo vim /etc/ansible/hosts
 
 scroll down
 
 enter:
 
 [Production]
 
 'slave EC2 name' ansible_ssh_host="ip address of slave/node'
 
 :wq! to save
 
 run command"
 
 ansible -m ping all
 
 sudo apt-get install sshpass
 
 sudo ansible 'server name' -m ping -vvv
