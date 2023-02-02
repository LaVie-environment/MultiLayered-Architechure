
Setting variables with a variables definition file. The variables definition file allows us to parameterize config code without having to hardcode default values.

The variables definition file consist of variable names and assignments.

The terraform.tfvars sets the namespace and region variables in variables.tf. The region variable configures the AWS provider