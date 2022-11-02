# AWS-MVP-eCommerce-Application
Project title:
Implementation of an E-Commerce System on AWS in an automated way using Terraform and Ansible
 
High-level Solution:
In this project, I worked as Cloud Engineer using DevOps, where I created and implemented an e-Commerce MVP (Minimum Viable Product) on AWS in less than 4 hours and in an automated way using Terraform and Ansible (Infrastructure as Code – IaC).

I provisioned the infrastructure in an automated way using Terraform and Ansible to automate the below
1. Configuration Management
2. Software Installation
3. Package Management of the EC2 instances.

In addition to above, Magento, PHP, MySQL, and Redis has been used to accomplish the project requirement.
######################################################################################
Flow of Steps:

1. Planning
2. Implementation
3. Go-Live
4. Post Go -live

![1](https://user-images.githubusercontent.com/26733874/199480192-8f20d548-03d0-4c11-89a5-2337eec67c08.png)



##########################################################################################
High Level Architecture
![2](https://user-images.githubusercontent.com/26733874/199480212-cab66c46-3882-44af-ab53-a3670b0a1ce9.png)


#########################################################################################

Hands-on Final Project - Part 1

E-commerce MVP deployment

1. Create Magento free account on:

https://marketplace.magento.com/ 

2. Create and Save the Public and Private Key from your Magento account.

3. Open AWS Cloud Shell

4. Install Terraform on AWS Cloud Shell

sudo yum install -y yum-utils
sudo yum-config-manager --add-repo https://rpm.releases.hashicorp.com/AmazonLinux/hashicorp.repo
sudo yum -y install terraform

5. Download the Terraform files on AWS Cloud Shell
mkdir final_project
cd final_project
wget <<upload terrafrom scripts in the project into S3 and download from there>>
unzip terraform.zip

6. Edit Terraform files | variable (same steps done in module 5):

- main.tf:
* variables

7. Running Terraform to deploy the EC2 VM:

cd terraform
terraform init
terraform plan
terraform apply

Hands-on Final Project - Part 2

- Connect to your EC2 instance via SSH

- Install Ansible in the EC2 VM

sudo yum-config-manager --enable epel
sudo yum install ansible -y

- Download the Ansible playbooks
wget <<upload ansible scripts in the project into S3 and download from there>>
unzip ansible

- Edit and save Ansible file parameters
cd ansible-magento2

File: group_vars/all.yml

* magento_domain
* server_hostname
* repo_api_key
* repo_secret_key

- Run Ansible to deploy the stack of tools for the e-commerce

cd ..
ansible-playbook -i hosts.yml ansible-magento2.yml -k -vvv --become

- Testing the E-commerce website:

Just copy and paste the EC2 Public IP in the browser.

*in some cases, it can take some minutes to get the website available!

- Setting up the e-commerce:
http://<EC2_PUBLIC_IP>/securelocation

User: Admin
Password: <<you can get this from magento files>>

(User and Password of the Magento Admin available in the file: group_vars/all.yml)

- Download the ecommerce images and personalize the ecommerce website.
<<upload images in the project into S3 and download from there>>

-- Content > Configuration > HTML Head > Edit (Default Store View)
--- Default page title: The Clodu Bootcamp Store
--- Header > Logo image: The Cloud Bootcamp logo from images
--- Header > Welcome text: Welcome to The Cloud Bootcamp Store!
--- Cache Refresh (Flush it)

-- Catalog > Products > Add product > The Cloud Bootcamp T-Shirt
--- Price: 80
--- Quantity: 100
--- Images And Videos > Add images
--- Save

-- Content > Pages > Edit Home Pages
--- Click Content > Erase content
--- Insert Widget > Widget type: Catalog New Products List > Insert Widget

--- Check if the customization is in place

- Capture the evidence.

- Think how you can innovate on this architecture (optional)

- Remove the resources deployed via AWS Cloud Shell

(If needed, re-install the Terraform following the same steps used previously)

cd ~/final_project/terraform
terraform destroy

Links:
Ansible Documentation: https://docs.ansible.com/ansible-core/devel/user_guide/index.html 
        
Once you done validating -- go ahead and destroy all the resources.      
