inside s3 folder

variable.tf

variable "my_env" {
  type        = string
  description = "env name"
}
variable "s3_bucket_count" {
  type        = number
  description = "Number of S3 buckets to create"
}




main.tf
resource "aws_s3_bucket" "my_s3_bucket" {
    count  = var.s3_bucket_count
    bucket = "${var.my_env}-s3-bucket-rama-2026-${count.index}"
    tags = {
        Name = "${var.my_env}-s3-bucket-rama-2026-${count.index}"
        Environment = var.my_env
    }
}

outputs.tf

output "bucket_id"{
    value = aws_s3_bucket.my_s3_bucket[*].id
    description = "the id of the s3 bucket"
}
output "bucket_region" {
    value = aws_s3_bucket.my_s3_bucket[*].region
}





-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

variables.tf

variable "my_env" {
    type = string
    description = "here env will come"
}
variable "dynamodb_count" {
    type = number
    description = "table creation count"
}

inside dynamodb folder.

main.tf

resource "aws_dynamodb_table" "my_dynamodb_table" {
    count = var.dynamodb_count
    name = "${var.my_env}-dynamodb-table-rama-2026-${count.index}"
    billing_mode = "PAY_PER_REQUEST"
    hash_key = "ID"
    attribute {
        name = "ID"
        type = "S"
    }
}

outputs.tf

output "dynamodb_table_name" {
  value       = aws_dynamodb_table.my_dynamodb_table[*].name
}
output "dynamodb_table_arns" {
  value       = aws_dynamodb_table.my_dynamodb_table[*].arn
  description = "ARNs of all DynamoDB tables"
}


--------------------------------------------------------------------------------------------------------------------------------------------------------------------

variables.tf

variable "my_env" {
  type        = string
  description = "env wise ec2 instance"
}
variable "instance_count" {
    type = number
    description = "number of ec2 instance"
}


outputs.tf

output "ubuntu_ami_name" {
  value       = data.aws_ami.ubuntu.name
  description = "The AMI Name being used"
}
output "instnace_name" {
    value = [for i in aws_instance.my_instance : i.tags["Name"]]
}
output "instance_volume" {
    value       = [for i in aws_instance.my_instance : i.root_block_device[0].volume_size]
}

inside ec2 folder
	
main.tf

data "aws_ami" "ubuntu" {
    most_recent = true
    filter {
        name = "name"
        values = ["ubuntu/images/hvm-ssd/ubuntu-*-*-amd64-server-*"]
    }
    filter {
        name   = "virtualization-type"
        values = ["hvm"]
    }
    owners = ["099720109477"]
}   
resource "aws_instance" "my_instance" {
    count = var.instance_count
    ami = data.aws_ami.ubuntu.id
    instance_type = "t3.micro"
    tags = {
        Name = "${var.my_env}-ec2-instance-rama-2026-${count.index}"
        Environment = var.my_env
    }
}

-----------------------------------------------------------------------------------------------------------------------------------------------

root level

main.tf


terraform {
  required_providers {
    aws = {
        source = "hashicorp/aws"
        version = "6.55"
    }
  }
  
}
provider "aws"{
    region = "ap-south-2"
}

locals {
  env = {
    dev = {
      bucket_count = 1
      dynamodb_count = 1
      instance_count = 2
    }
    stage = {
      bucket_count = 1
      dynamodb_count = 1
      instance_count = 3
    }
    prod = {
      bucket_count = 2
      dynamodb_count = 2
      instance_count = 4
    }
  }  
}
module "s3" {
  source = "./modules/s3"
  my_env           = terraform.workspace
  s3_bucket_count  = local.env[terraform.workspace].bucket_count
}
module "dynamodb" {
  source = "./modules/dynamodb"
  my_env = terraform.workspace
  dynamodb_count  = local.env[terraform.workspace].dynamodb_count
}
module "ec2" {
  source = "./modules/ec2"
  my_env = terraform.workspace
  instance_count = local.env[terraform.workspace].instance_count
}

terraform workspace new dev
terraform workspace new stage
terraform workspace new prod

terraform workspace select dev
terraform workspace select stage
terraform workspace select prod

terraform workspace list
terraform workspace show


Goal accomplished

outputs.tf


output "s3_bucket_ids" {
    value = module.s3.bucket_id
}
output "s3_bucket_name" {
    value = module.s3.bucket_region
}
output "dynamodb_table_name" {
    value = module.dynamodb.dynamodb_table_name
}
output "dynamodb_table_arns" {
    value = module.dynamodb.dynamodb_table_arns
}
output "ec2_instance_name" {
    value = module.ec2.instnace_name
}
output "ec2_volume_size" {
    value = module.ec2.instance_volume
}
output "ec2_image_name" {
    value = module.ec2.ubuntu_ami_name
}

GAL
.
.<img width="1348" height="3873" alt="image" src="https://github.com/user-attachments/assets/3adba2ab-b0e9-4a61-912c-27b3984c22c3" />
