# cloud-computing

minimum requirements:
- ansible 2.9.6 or higher
- ubuntu 20.04 Focal Fossa

This project deploys the web application app1.py and the output is shown at port 8000.  

Steps:
- Create 5 servers with ' HAproy, Bastion, devA, devB and devC ' on any cloud platform. Make sure of the case used for the server names.
- In the 'config' file above, make sure to insert HostName for all servers with respective descriptions. Example is shown below 
Host Bastion
   User ubuntu
   HostName 91.106.195.180
   IdentityFile ~/.ssh/id_rsa
   UserKnownHostsFile /dev/null
   StrictHostKeyChecking no
   PasswordAuthentication no

Host HAproxy
   User ubuntu
   HostName 10.1.0.109
   IdentityFile ~/.ssh/id_rsa
   StrictHostKeyChecking no
   PasswordAuthentication no
   ProxyJump Bastion

Host devA
   User ubuntu
   HostName 10.1.0.157
   IdentityFile ~/.ssh/id_rsa
   UserKnownHostsFile=/dev/null
   StrictHostKeyChecking no
   PasswordAuthentication no
   ProxyJump Bastion

Host devB
   User ubuntu
   HostName 10.1.0.79
   IdentityFile ~/.ssh/id_rsa
   UserKnownHostsFile=/dev/null
   StrictHostKeyChecking no
   PasswordAuthentication no
   ProxyJump Bastion

Host devC
   User ubuntu
   HostName 10.1.0.117
   IdentityFile ~/.ssh/id_rsa
   UserKnownHostsFile=/dev/null
   StrictHostKeyChecking no
   PasswordAuthentication no
   ProxyJump Bastion



   - after creation of servers and editing config file, one can deploy the web application by just one command
-----------------------------------
ansible-playbook -i hosts site.yml
-----------------------------------
  
  - one can also check the successful deployment by the command
------------------------------
curl <HAproxy Public IP>:8000
---------------------------------
or one can also check <HAproxy Public IP>:8000 on any of their favourite browser
<HAproxy Public IP>:8000
Example:
103.57.74.38:8000
