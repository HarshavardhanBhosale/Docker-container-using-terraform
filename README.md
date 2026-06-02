# Terraform Docker Container using IaC

## Objective

This project demonstrates Infrastructure as Code (IaC) using Terraform and Docker.
Terraform is used to provision and manage a local Docker container running Nginx.

---

# Tools & Technologies

* Terraform
* Docker
* Nginx
* GitHub

---

# Project Structure

```bash
terraform-docker-container/
│
├── .terraform/
├── screenshots/
├── .terraform.lock.hcl
├── main.tf
├── terraform.exe
├── terraform.tfstate
├── terraform.tfstate.backup
└── README.md
```

---

# Terraform Configuration

## main.tf

```hcl
terraform {
  required_providers {
    docker = {
      source  = "kreuzwerker/docker"
      version = "~> 3.0.2"
    }
  }
}

provider "docker" {}

resource "docker_image" "nginx_image" {
  name = "nginx:latest"
}

resource "docker_container" "nginx_container" {
  name  = "terraform-nginx-container"
  image = docker_image.nginx_image.image_id

  ports {
    internal = 80
    external = 8080
  }
}
```

---

# Steps Performed

## 1. Initialize Terraform

```bash
terraform init
```

This command downloads required providers and initializes Terraform.

---

## 2. Validate Terraform Code

```bash
terraform validate
```

Checks whether the Terraform configuration is valid.

---

## 3. Preview Infrastructure Changes

```bash
terraform plan
```

Shows what resources Terraform will create before deployment.

---

## 4. Create Docker Infrastructure

```bash
terraform apply
```

Type:

```bash
yes
```

Terraform pulls the Nginx image and creates a Docker container.

---

## 5. Verify Running Container

```bash
docker ps
```

Checks whether the container is running successfully.

---

## 6. Check Terraform State

```bash
terraform state list
```

Displays all Terraform-managed resources.

---

## 7. Destroy Infrastructure

```bash
terraform destroy
```

Type:

```bash
yes
```

Removes the Docker container and related resources.

---

# Output

After successful deployment:

* Docker container runs locally
* Nginx server accessible on:

```bash
http://localhost:8080
```

---

# Screenshots

Project execution screenshots are available inside the `screenshots/` folder.

---

# Learning Outcomes

* Learned Infrastructure as Code (IaC)
* Understood Terraform workflow
* Managed Docker containers using Terraform
* Worked with Terraform state management
* Automated infrastructure provisioning

---

# Author

Harshavardhan Bhosale
