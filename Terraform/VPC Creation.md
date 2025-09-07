---
Title: VPC Creation with Terraform
tags:
  - terraform
  - AWS
date: 2025-02-16
---

VPC Consist of 4 main component
- subnet
- route tables
- NAT gateways/ internet gateways
- subnet associations

### main.tf

```
# vpc
resource "aws_vpc" "main" {
  cidr_block       = var.vpc_cidr

  tags = {
    Name = "${var.tag}-vpc"
  }
}

data "aws_availability_zones" "available" {
  state = "available"
}

# public subnet

resource "aws_subnet" "main" {
  count = length(var.public_subnet_cidr)
  vpc_id     = aws_vpc.main.id
  availability_zone = data.aws_availability_zones.available.names[count.index]
  cidr_block = element( var.public_subnet_cidr, count.index )
  tags = {
    Name = "${var.tag}-public-subnet-${element( var.public_subnet_cidr, count.index )}"
  }
}

## private subnet
resource "aws_subnet" "private" {
    count = length(var.private_subnet_cidr)
  vpc_id     = aws_vpc.main.id
  availability_zone = data.aws_availability_zones.available.names[count.index]
  cidr_block = element(var.private_subnet_cidr, count.index)

  tags = {
    Name = "${var.tag}-private-subnet-${element(var.private_subnet_cidr, count.index)}"
  }
}

# public rt

resource "aws_route_table" "main" {
  vpc_id = aws_vpc.main.id

  route {
    cidr_block = "0.0.0.0/0"
    gateway_id = aws_internet_gateway.gw.id
  }


  tags = {
    Name = "${var.tag}-public-route"
  }
}


# private rt

resource "aws_route_table" "private" {
  vpc_id = aws_vpc.main.id

  route {
    cidr_block = "0.0.0.0/0"
    gateway_id = aws_nat_gateway.nat.id
  }


  tags = {
    Name = "${var.tag}-private-route"
  }
}
# eip
resource "aws_eip" "nat" {
  domain   = "vpc"
} 

#nat 
resource "aws_nat_gateway" "nat" {
  allocation_id = aws_eip.nat.id
  subnet_id     = aws_subnet.main[0].id

  tags = {
    Name = "${var.tag}-nat"
  }


  depends_on = [aws_internet_gateway.gw]
}

# igw 
resource "aws_internet_gateway" "gw" {
  vpc_id = aws_vpc.main.id

  tags = {
    Name = "${var.tag}-igw"
  }
}

# subnet association

resource "aws_route_table_association" "a" {
  count = length(var.public_subnet_cidr)
  subnet_id = aws_subnet.main[count.index].id
  route_table_id = aws_route_table.main.id
}

# private subnet association

resource "aws_route_table_association" "b" {
  count = length(var.private_subnet_cidr)
  subnet_id      = aws_subnet.private[count.index].id
  route_table_id = aws_route_table.private.id
}
```

### Var.tf
```
variable "vpc_cidr" {
  type = string
  description = "vpc cidr"
  default = "10.0.0.0/16"
}

variable "tag" {
  type = string
  default = "cdec"
}

variable "public_subnet_cidr" {
  default = ["10.0.1.0/24", "10.0.2.0/24"]
}

variable "private_subnet_cidr" {
  default = ["10.0.3.0/24", "10.0.4.0/24", "10.0.5.0/24","10.0.6.0/24"]
}
```

### providers.tf
```
terraform {
  required_providers {
    aws = {
      source = "hashicorp/aws"
      version = "5.85.0"
    }
  }
}

provider "aws" {
  #Configuration options
  region = "us-east-1"

}
```
### Output.tf
```
output "vpc_id" {
  value = aws_vpc.main.id
}

output "public_subnet_id" {
  value = aws_subnet.main[*].id
}
output "private_subnet_id" {
  value = aws_subnet.private[*].id
}
```

