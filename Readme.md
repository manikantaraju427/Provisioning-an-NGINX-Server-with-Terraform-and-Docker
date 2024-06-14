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

* In the working directory, create a file called main.tf

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




