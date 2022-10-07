### Basic terraform 

A basic terraform code which creates an ec2 instance in us-west-2 region in AWS cloud provider

```javascript
terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 4.16"
    }
  }

  required_version = ">= 1.2.0"
}

variable "region" {
  default     = "us-west-2"
  description = "Enter AWS region "
}

variable "imageId" {
  type        = string
  description = "Enter AWS EC2 imageid "
  default     = "ami-830c94e3" #ami = "ami-08d70e59c07c61a3a"
}

variable "instanceType" {
  type        = string
  description = "Enter AWS EC2 instance type "
  default     = "t2.micro"
}

provider "aws" {
  region = var.region
}

resource "aws_instance" "app_server" {
  ami           = var.imageId
  instance_type = var.instanceType

  tags = {
    Name = "AppServer"
  }
}

output "app_server_ip_addr" {
  value = aws_instance.app_server.private_ip
}

```

Terraform code creates 2 sns topic in 2 aws region 

```javascript
provider "aws" {
  alias  = "us-east-1"
  region = "us-east-1"
}

provider "aws" {
  alias  = "us-west-2"
  region = "us-west-2"
}

resource "aws_sns_topic" "topic-us-east" {
  provider = aws.us-east-1
  name     = "topic-us-east"
}

resource "aws_sns_topic" "topic-us-west" {
  provider = aws.us-west-2
  name     = "topic-us-west"
}
```