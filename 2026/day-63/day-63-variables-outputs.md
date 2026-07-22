if write count=10, it creates 10 instance in a second and for deleteing also just have to write terraform destroy


resource "aws_instance" "my_ec2_instance" {
  count = 10
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


Terraform is declarative

after that I stored state file in s3 bucket and 


backend "s3" {
    bucket         = "s3-demo-bucket-rama-2026"   
    key            = "terraform.tfstate"      
    region         = "ap-south-2"                  
    dynamodb_table = "terra-state-table"             
                       
  }



variable "state_table_name" {
  type = string
  default  = "terra-state-table"
}
resource "aws_dynamodb_table" "my_state_table" {
  name           = var.state_table_name
  billing_mode   = "PAY_PER_REQUEST"   
  hash_key       = "LockID"
  attribute {
    name = "LockID"
    type = "S"
  }
  tags = {
    Name = var.state_table_name
  }
}

