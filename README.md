
The variables.tf file defines the variables for the Terraform configuration. It consists of variable names and assignments.

The assignments of values to the variables takes place in the Terraform.tfvars file.


The networking module provisions all networking-related components of the web app, Virtual Private Cloud (VPC), subnets, Internet gateway, and security groups.
It takes the namespace as an input and outputs vpc, and security group.

Resources declared at the top of the module have the fewest dependencies, while resources declared at the bottom have the most dependencies.

The VPC and the db security group IDs which are outputs of the networking module are passed to the database module. Data are passed to the db module by bubbling up from the networking module into the root module and then trickling down into the database module.

The root module declares component modules and allows those components modules to pass data between themselves.