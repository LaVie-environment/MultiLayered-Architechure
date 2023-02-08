
The variables.tf file defines the variables for the Terraform configuration. It consists of variable names and assignments.

The assignments of values to the variables takes place in the Terraform.tfvars file.


The networking module provisions all networking-related components of the web app, Virtual Private Cloud (VPC), subnets, Internet gateway, and security groups.
It takes the namespace as an input and outputs vpc, and security group.

Resources declared at the top of the module have the fewest dependencies, while resources declared at the bottom have the most dependencies.

The VPC and the db security group IDs which are outputs of the networking module are passed to the database module. Data are passed to the db module by bubbling up from the networking module into the root module and then trickling down into the database module.

The root module declares component modules and allows those components modules to pass data between themselves.

The autoscaling module provisions the autoscaling group, load balancer, Identity and Access Management (IAM) instance role and everything else the web server needs to run.
The three input variables of the autoscaling module are vpc, sg, and db_config. The vpc, and sg come from the networkng module, while db_config comes from the database module.

Using a cloudinit_config data source to create the launch template's user data.
The launch template bundles together user data, the MI ID, and other metadata

The result of the templatefile function is passed into the cloudinit_config data source and then used to configure the aws_template resource.
The templatefile function accepts two arguments: a path and a variable object.