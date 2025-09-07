---
Title: Ec2 Creation
tags:
  - terraform
  - EC2
date: 2025-02-16
---
Terraform is IAC i.e. Infrastructure as Code which leverages code to create Infrastructure resource in any of the cloud provider that support terraform.

We create two files `main.tf` and `provider.tf` 
in `main.tf` we specify the resources with their configuration to create and in `provider.tf` we declare information about the cloud provider at we are creating resources.

Here is the simple Terraform code to create `aws_instance` resource in aws platform.

File Name: `main.tf`
```tf
resource "aws_instance" "a" {
  ami           = "ami-0c614dee691cbbf37"
  instance_type = "t2.micro"
  key_name = "my-key"

  tags = {
    Name = "HelloWorld"
  }
}
```

File Name: provider.tf
```tf
terraform {
  required_providers {
    aws = {
      source = "hashicorp/aws"
      version = "5.80.0"
    }
  }
}

provider "aws" {
  region = "us-east-1"
}
```

To apply the execution plan we run 
`terraform plan` This shows us detailed view of what changes going to take place.
and with `terraform apply` we make these changes.

