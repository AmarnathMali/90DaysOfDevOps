Intro to Terraform

	- what is Terraform?
	=> Infrastructure as Code Tool, which provisions infrastructure though code, without manual clicks and reduces overall time.
	- IAC Tools in market: Terraform, CloudFormation, OpenTofu, Pulumi, Ansible, Crossplane
	- why infrastructure code matters?
	- Terraform lifecycle and workflow?
	- Terraform vs Ansible
	=> Terraform creates infrastructure and ansible configures 
	- Terraform vs CloudFormation
	=> Primary tool for creation  IAS for AWS is Cloud Formation, Terraform is used to  create Aws, Azure, GCP etc.
	- Terraform vs OpenTofu
	=> OpenTofu is same, similar of Terraform, and it is made from Terraform code only
	- where Terraform fits in modern DevOps
	=> Modern DevOps needs automation, reduction of time to market, scaling that's why Terraform comes in picture.
	
	
	
	Installed Terraform on EC2 instance
	
	its simple just search terraform install in browser, open link of Terraform offical
	in that choose machine steps according to you
	paste those and install
	check terraform --version
	
	to connect terraform to aws it reqires aws cli
	lets download that to, sear aws cli install
	and follow the steps in documentation and you are good to go
	
	tried doing aws login that is not working
	so aws configure which asks aws access key id
	for that go to iam and created access key id and password  and connected 
	
	
	
Terraform 
#Hashicrop Configuration language

block:
	- resource
	- output
	- variable
	- data
	- terraform

parameters
	- resource name
	- resource type

arguments:
	- configuration
	
	
	
Example:
created s3 bucket:

vim main.tf
	resource "aws_s3_bucket" "my_s3_bucket" {
	  bucket = "s3-demo-bucket-rama-2026"
	}

terraform init       -> to initialize the terraform it is first step
	- it creates .terraform folder
terraform plan
terraform apply


	
