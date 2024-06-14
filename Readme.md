# Provisioning an NGINX Server with Terraform and Docker

# Install Terraform

1) Update the package list:

$sudo apt-get update

2) Install required dependencies:

$sudo apt-get install -y gnupg software-properties-common

3) Add the HashiCorp GPG key:

$wget -O- https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg

4) Add the official HashiCorp Linux repository:

$echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list

5) Update the package list again to include the new repository:

$sudo apt-get update

6) Install Terraform:

$sudo apt-get install terraform

7) verify the installation by checking the Terraform version:

$terraform -v

![Screenshot (439)](https://github.com/manikantaraju427/Provisioning-an-NGINX-Server-with-Terraform-and-Docker/assets/125948783/43ffc6a8-36f2-4827-817b-58a8edee09ac)



