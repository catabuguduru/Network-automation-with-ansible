# Network-automation-with-ansible

This task is to deploy nginx servers on 3 web servers using Bastion Host and HAproxy. The nginx servers should be deployed using ansible playbook and deployed in the city cloud.

### Clone the github repository

### Creating ssh key pairs and servers 
 To create the server, we must create the keypairs. For key pair genertaion in the cloud, First we need to generate the public key in our local host system. The commands used are:
 ```
 ssh-keygen -C secret
 cp secret ~/.ssh/
 ```
 The created key must be stored in the .ssh. I have used the same key secret for all my 5 hosts. The public key is used in citycloud network to create keypair.
  
