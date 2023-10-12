Terraform normally loads all of the `.tf` and `.tf.json` files within a directory and expects each one to define a distinct set of configuration objects. If two files attempt to define the same object, Terraform returns an error.
Examples:
* `main.tf`
* `outputs.tf`
* `variables.tf.json`
Types and Examples:
1. **Main Configuration file( `main.tf` )**
The main Terraform configuration file, `main.tf`, can look something like this:
```hcl
# AWS Provider 
provider "aws" {
  region = "us-west-2"
}

# Create an EC2 instance
resource "aws_instance" "example" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"
}
```
2. **Variable Files (`.tfvars`)**: A variable file `dev.tfvars` can contain variable values for the "dev" environment:
```hcl
# dev.tfvars
region = "us-east-1"
environment = "dev"
```
3. **Variable Declaration Files (`.tf`)**: A variable declaration file `variables.tf` can contain variable definitions and their default values:
```hcl
# variables.tf
variable "region" {
  description = "AWS region"
  default     = "us-east-1"
}
```
4. **Module Configuration Files (`.tf`)**: In a module configuration file `vpc_module.tf`, you can define resources and variables for the module:
```hcl
# vpc_module.tf
module "vpc" {
  source = "./modules/vpc"
  vpc_cidr = var.vpc_cidr
}
```
5. **Provider Configuration Files (`.tf`)**: A provider configuration file `aws.tf` can contain settings for the AWS provider:
```hcl
# aws.tf
provider "aws" {
  region = "us-west-2"
}
```
6. **State Files (`terraform.tfstate`)**: The Terraform state file `terraform.tfstate` contains information about the current state of infrastructure and is typically not edited manually.
7. **Output Files (`.tf`)**: An output file `outputs.tf` can define output variables that can be used by other tools or processes:
```hcl
# outputs.tf
output "instance_id" {
  value = aws_instance.example.id
}
```