for this I created variable.tf file

the block is variables and arguments we can give anything and for defining name we have to use default and type string or number


variable "my_ec2_instance_name" {
  type        = string
  default     = "terra-server"
  description = "this variable holds the ec2 instance name"
}
variable "my_ec2_volume_size" {
  type        = number
  default     = 10
  description = "holds the ec2 volume size"
}


I used these variable to create ec2 instance

how  to use  "var.my_ec2_instance_name" like this , ha this is called interpolation


ubuntu@ip-172-31-13-15:~/Terraform-Practice$ terraform state list
data.aws_ami.ubuntu
aws_default_vpc.default
aws_dynamodb_table.my_state_table
aws_instance.my_ec2_instance
aws_key_pair.my_ec2_key
aws_s3_bucket.my_s3_bucket
aws_security_group.my_ec2_sg
aws_vpc_security_group_egress_rule.allow_all_traffic_ipv4
aws_vpc_security_group_ingress_rule.allow_http
aws_vpc_security_group_ingress_rule.allow_ssh


terraform state list is showing you all the resources Terraform is currently tracking in its state file

output file:
to get output like public ip address etc,
in terraform, output.tf file we can use

output "my_ec2_public_ip" {
	value = aws_instance.my_ec2_instance.public_ip
}


to check output we have to do terraform apply, to move this in state after that we can use terraform output
