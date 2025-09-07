---
Title: S3 Buckets Creation
tags:
  - S3
  - terraform
date: 2025-02-16
---
There are two methods to do this:
1. Manually giving buckets names for each buckets
2. Using Increment in Variable to add numbers after specific Unique name

## Method 1 : Manually Adding Bucket Names

**Filename:** Main.tf

```tf
resource "aws_s3_bucket" "my-known-buckets" {
  count     = length(var.bucket_names) 
  bucket    = var.bucket_names[count.index]
}
```

**Filename:** vars.tf
```tf
variable "bucket_names" {
  description = "List of S3 bucket names"
  type        = list(string)
  default     = ["chandratsdfsdasfdfaara", "nayantara123qq3112", "rocketshopzxys", "123asdxzsdgheoi", "asdf21alkj44dsfj"]
}
```

**Filename:** provider.tf
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
  # Configuration options
  region = "us-east-1"
}
```

This will create 5 buckets with the given names `["chandratsdfsdasfdfaara", "nayantara123qq3112", "rocketshopzxys", "123asdxzsdgheoi", "asdf21alkj44dsfj"]`

Apply it using 
`terraform plan`
`terraform apply`

You can list s3 buckets with aws cli commands
```bash
aws s3 ls
```

## Method 2: Using Increment in Variable to add numbers after specific Unique name

Use this method when you have too many buckets to create and naming doesnt really matters
then this will save your time as you only need to change bucket count in `vars.tf` file

**Filename:** main.tf

```tf
resource "aws_s3_bucket" "c" {
  count     = var.bucket_count
  bucket    = "wingardiumleviosamybucketsintheair-${count.index + 1}"
}
```

**Filename:** vars.tf
```tf
variable "bucket_count" {
	description = "number of s3 buckets to create"
	type = number
	default = 5
}
```
