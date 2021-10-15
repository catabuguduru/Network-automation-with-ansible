# Network-automation-with-ansible

This task is to deploy nginx servers on 3 web servers using Bastion Host and HAproxy. The nginx servers should be deployed using ansible playbook and deployed in the city cloud.

### Clone the github repository

Clone the repository https://github.com/catabuguduru/Network-automation-with-ansible.git using git clone command

### Creating ssh key pairs and servers 
 To create the server, we must create the keypairs. For key pair genertaion in the cloud, First we need to generate the public key in our local host system. The commands used are:
 ```
 ssh-keygen -C secret
 cp secret ~/.ssh/
 ```
 The created key must be stored in the .ssh. I have used the same key secret for all my 5 hosts. The public key is used in citycloud network to create keypair.
 
 Create the servers in the city cloud using secret keypair(created in city cloud) and select a network. Need to create 5 hosts named HA server and bastionET2598 (give floating IP address), server A,B,C.
 
 Note-After creating the servers try ssh to bastionET2598 and check the connection among the servers
  
  ### Setting up the Local DNS setup
  Edit the following files in your system (sudo nano /etc/hosts) and enter the IP's and corresponding names of your webservers and hosts.
  ```
 188.95.227.101 bastionET2598
 188.95.227.115 HAserver
 10.1.0.115 serverA
 10.1.0.185 serverB
 10.1.0.18 serverC
 ```
 ### Setting up the Bastion Host
 
 run the following command to add the public key to the server.
 ```
 rsync -avz ~/.ssh/secret bastionET2598@188.95.227.101:~/.ssh/id_rsa
 ```
 As how we set up the /etc/hosts in the local system do the same in the bastion host by ssh into it.
 
 #### Add the config file in /.ssh/config. 
 The config file can be found as configfile.
 
 ### Create the ansible playbook
 Make sure the hosts and site.yaml is written and the installation packages required for deployment has to be upgraded.
 
 
 ### Run the ansible playbook 
- Once everything is configured run ansible playbook named site.yaml with the following commands to deploy HAProxy & Nginx web servers.
```
cd ~/creator && ansible-playbook -i hosts site.yaml
```

After the completion of deployment, you can check the status using the following URL

http://188.95.227.115/
 

  
