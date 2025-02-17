# Automating-RDS-Database-Using-Terraform
# Project Overview
This project automates the creation of an Amazon RDS instance using Terraform on a CentOS 7 EC2 instance.

**Prerequisites**
1. AWS Account
2. EC2 Instance (CentOS 7)
3. IAM User with Access Key and Secret Key
4. Terraform (installed in the instance after launching)
5. MySQL Workbench for DB connection

**Setup & Execution**
1. Launch EC2 Instance, Start a CentOS 7 instance in AWS.
2. Install Terraform
**sudo yum install -y yum-utils
sudo yum-config-manager --add-repo https://rpm.releases.hashicorp.com/RHEL/hashicorp.repo
sudo yum -y install terraform**
3. Create a Terraform Project Directory
mkdir terraform-project
cd terraform-project
4. Create variables.tf: Create a file using vi and name it variables.tf and define variables for AWS access keys and other required inputs.
5. Create main.tf: Create a file main.tf and define the RDS instance configuration.
6. Initialize and Apply Terraform
**terraform init
terraform validate
terraform plan
terraform apply**
Type yes when prompted.
7. Verify RDS Instance
Go to the RDS Console in AWS and confirm the instance is created. Copy the endpoint for later connection.
8. Connect to RDS via MySQL Workbench
Install MySQL Workbench. Manage connections --> Enter the details:
Connection name: can be kept anything
Hostname: endpoint of rds
username: one which we gave in putty in “main.tf” and after clicking on store in vault 

Now, we can enter  password the same which we gave in “main.tf”. Click on test connection. If connection fails, update Security Group inbound rules to allow port 3306 from anywhere i.e. Type: MYSQL/Aurora.

**Troubleshooting:**
Ensure Access and Secret Keys are correct. Verify Terraform scripts for syntax errors. Adjust Security Group settings for database access.

**Expected Output:**
Successful RDS instance creation visible on AWS Console.
Accessible MySQL database using Workbench.
