## Fall 2022 - DevOps Lab 1
### Infrastructure Provisoning using Terraform and Azure Cloud
In this tutorial, we will be using Terraform to provision an Azure Virtual Machine Instance.
The following steps assume that you have created an **SSH Key** in your Azure Portal and copied the public key to your Azure Cloud Shell .ssh directory.

All commands will be executed in your **Azure Cloud Shell**.

1. Clone the project

        git clone https://github.com/msambou/infrastructure-provisioning-azure-terraform

2. Change directory into the project directory

        cd infrastructure-provisioning-azure-terraform

3. Modify the public key path in main.tf

        code main.tf
    
    In the admin_ssh_key block, enter the path to the SSH public key you copied to the Azure Cloud Shell.

4. Run the command below to initialize terraform

        terraform init

5. Run the command below to apply the deployment

        terraform apply

6. You will terminate the resources you created at the end of the Lab Session.
To destroy the resources created, run the command below.

        terraform destroy









