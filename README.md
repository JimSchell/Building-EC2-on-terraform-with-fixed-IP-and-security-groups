# Building-EC2-on-terraform-with-fixed-IP-and-security-groups

•	Create a DB Server and output the private IP


•	Create a web server and ensure it has a fixed public IP


•	Create a Security Group for the web server opening ports 80 and 443 (HTTP and HTPPS)


•	Run a script for the web server

First thing I’ve done is upload the script to run the web server; below demonstrates its going to upload the system, install Apache, enabled is activated this is if the webserver ever goes down it will restart and finally the ‘echo’ line is what we will see on the web page.

![image](https://github.com/user-attachments/assets/3aa999c4-7647-4509-b87d-5ec191e35baf)


After the script is uploaded, I start by creating the resource and selecting the provider, I also attached the AMI I’m using for the EC2 instance. I have attached a tag as well stating “DB Server” 


![image](https://github.com/user-attachments/assets/7b067f0a-8dea-4e38-a697-e04706f13b84)

Once the two webservers are inputed, I now need to create my EIP (Elasitc IP) 


![image](https://github.com/user-attachments/assets/a7d29488-dfd3-4fc3-8b27-ea1345bd61b4)

Now I need to set up the security groups and to do this I will use dynamic block, firstly I need to set up the variables, there will be two an ‘ingress’ and ‘egress’ both enabling ports 80 and 443


![image](https://github.com/user-attachments/assets/dcab2d97-5347-40b0-9b40-4155ba9dbb48)

Now I setup the security group, allowing web traffic, this is where is set up dynamic block - I want to allow everything so I set the cidr range 0.0.0.0,0

![image](https://github.com/user-attachments/assets/85f56edf-9c61-497b-864b-5d681f78b6ff)

Once the security groups are set up I need to attach the security group to the web instance and I also attach the script to the web instance 

![image](https://github.com/user-attachments/assets/7a1e00ae-bee3-4163-92e2-c704499833aa)

Lastly, I attach a couple of outputs

![image](https://github.com/user-attachments/assets/b9eb5f49-7079-4ff6-bd75-37ec9bd4d2bc)

Once I’m happy everything is in place, and before I confirm on Terraform apply – what will happen, the EIP will be created - DB instance - web server - security group with ports 443 and 80

![image](https://github.com/user-attachments/assets/35d57bde-2b82-4837-84bc-24d8c3b26933)




























