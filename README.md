# Terraform Docker Container Project

## Objective

Provision a local Docker container using Terraform Infrastructure as Code (IaC).

---

# Tools Used

* Terraform
* Docker

---

# Project Structure

```bash
terraform-docker-container/
│
├── main.tf
├── provider.tf
├── variables.tf
├── outputs.tf
├── .gitignore
├── screenshots/
└── README.md
```

---

# Terraform Files

## provider.tf

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
```

---

## main.tf

```hcl
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

# Commands Used

## Initialize Terraform

```bash
terraform init
```

## Validate Configuration

```bash
terraform validate
```

## Preview Infrastructure

```bash
terraform plan
```

## Create Infrastructure

```bash
terraform apply
```

## Check Running Container

```bash
docker ps
```

## Check Terraform State

```bash
terraform state list
```

## Destroy Infrastructure

```bash
terraform destroy
```

---

# Output

* Docker container created successfully
* Nginx application accessible on localhost:8080
* Infrastructure managed using Terraform

---

# Learning Outcome

* Understood Infrastructure as Code
* Learned Terraform workflow
* Managed Docker containers using Terraform
* Learned state management in Terraform
