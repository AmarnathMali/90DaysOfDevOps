the state which maps the configuration and actual infrastructure resources. and it stores every info about that infrastructure.

terraform init, when we do the first line shows initializing the backend why?
	- Terraform needs to set up where and how it will store the state file  (terraform.tfstate).
	- Terraform uses to store, load, and update state. It can be local (a file on disk) or remote (S3, Azure Blob, GCS, Terraform Cloud, etc.).
	- default it store in local project folder
	
	
	
	
	block parameters {
	   Arguments
	}
	
##configure aws 

	terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 6.0"
    }
  }
}
	 
	
now let's create ec2 instance, what are the things required for it?

	- AMI (Amazon machine image) - done
	- instance type  (t3.micro)
	- key pair   - done
	- vpc and subnet  -> done default used
	- storage/volume
	- security group (inbound (ingress) / outbound (egress)) - done
	- region (provider)
	- tag , name

key pair:
	resource aws_key_pair my_ec2_key {
	    key_name = "terra-server-key"
	    public_key = file(terra-server-key.pub)
	}
	
ami:
	data aws_ami ubuntu {
	    most_recent = true
	
	    filter {
	        name = "name"
	        values = ["ubuntu/images/hvm-ssd/ubuntu-focal-26.04-amd64-server-*"]
	    }
	
	    filter {
	        name   = "virtualization-type"
	        values = ["hvm"]
	    }
	
	    owners = ["099720109477"] # Canonical
	}

vpc:
resource "aws_default_vpc" "default" {
 }

Security Group:


resource "aws_security_group" "my_ec2_sg" {
  name        = "terra-server-sg"
  description = "Allow TLS inbound traffic and all outbound traffic"
  vpc_id      = aws_default_vpc.default.id  #interpolation
  tags = {
    Name = "terra-server-sg"
  }
}

# inbound rule (ingress)

resource "aws_vpc_security_group_ingress_rule" "allow_ssh" {
  security_group_id = aws_security_group.my_ec2_sg.id
  cidr_ipv4         = "0.0.0.0/0"
  from_port         = 22
  ip_protocol       = "TCP"
  to_port           = 22
}

# outbound rule (egress)


resource "aws_vpc_security_group_egress_rule" "allow_all_traffic_ipv4" {
  security_group_id = aws_security_group.my_ec2_sg.id
  cidr_ipv4         = "0.0.0.0/0"
  ip_protocol       = "-1" # semantically equivalent to all ports
}

#create ec2 instance


resource "aws_instance" "my_ec2_instance" {
  ami           = data.aws_ami.ubuntu.id
  instance_type = "t3.micro"
  vpc_security_group_ids = [aws_security_group.my_ec2_sg.id]
  key_name = aws_key_pair.my_ec2_key.id
  root_block_device {
    volume_size           = 50
    volume_type           = "gp3"
  }
  tags = {
    Name = "terra-server"
  }
}
given vpc aand ec2 full access to iam user
it created:


	
<img width="1327" height="3157" alt="image" src="https://github.com/user-attachments/assets/c78accd8-21a9-456b-b4d0-f4c5f4c6dd69" />
