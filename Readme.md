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

* Create a directory named learn-terraform-docker-container.

$mkdir learn-terraform-docker-container
![Screenshot (440)](https://github.com/manikantaraju427/Provisioning-an-NGINX-Server-with-Terraform-and-Docker/assets/125948783/7978b91c-c264-4a3a-8c57-2ee27e591b0f)

* Navigate into the working directory.

$cd learn-terraform-docker-containe
![Screenshot (441)](https://github.com/manikantaraju427/Provisioning-an-NGINX-Server-with-Terraform-and-Docker/assets/125948783/9481920b-6c16-4c9a-8d8f-fe57d5da690b)

* In the working directory, create a file called

* main.tf

terraform {

required_providers {

docker = {

source = “kreuzwerker/docker”

version = “~> 3.0.1”

}

}

}

provider “docker” {}

resource “docker_image” “nginx” {

name = “nginx”

keep_locally = false

}

resource “docker_container” “nginx” {

image = docker_image.nginx.image_id

name = “tutorial”

ports {

internal = 80

external = 8000

}

}
![Screenshot (442)](https://github.com/manikantaraju427/Provisioning-an-NGINX-Server-with-Terraform-and-Docker/assets/125948783/91b1cf9b-4753-4456-9ca5-93362397ebe0)

* Initialize the project, which downloads a plugin called a provider that lets Terraform interact with Docker.

$terraform init
![Screenshot (443)](https://github.com/manikantaraju427/Provisioning-an-NGINX-Server-with-Terraform-and-Docker/assets/125948783/efc66d80-a166-449d-b539-c0257e3c8d9e)


$terraform plan

* Provision the NGINX server container with apply. When Terraform asks you to confirm type yes and press ENTER.
  
$terraform apply
![Screenshot (444)](https://github.com/manikantaraju427/Provisioning-an-NGINX-Server-with-Terraform-and-Docker/assets/125948783/7ee27f2b-a592-435d-a585-edfc78f727e6)

Verify the existence of the NGINX container by visiting 65.0.133.237:8000 in my web browser or running docker ps to see the container.
![Screenshot (446)](https://github.com/manikantaraju427/Provisioning-an-NGINX-Server-with-Terraform-and-Docker/assets/125948783/56afcdf4-17ec-4ade-a5aa-2a14d3f483ab)

* docker ps to see the container.
![Screenshot (447)](https://github.com/manikantaraju427/Provisioning-an-NGINX-Server-with-Terraform-and-Docker/assets/125948783/60b397b7-1d58-467c-a5ad-8f75b3dc9815)

* To stop the container, run terraform destroy.

$terraform destroy
![Screenshot (448)](https://github.com/manikantaraju427/Provisioning-an-NGINX-Server-with-Terraform-and-Docker/assets/125948783/04368590-5548-4234-b3c0-e5f854ea8466)


# Thank you for reading!




