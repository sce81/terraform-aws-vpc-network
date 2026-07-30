# terraform-module-aws-vpc
Terraform module for AWS VPC


## Getting Started

This module is intended to create an AWS VPC with up to 3 subnet tiers

Resources
- aws_vpc
- aws_subnet


### Prerequisites

Terraform ~> 1.0.0

### Tested

Terraform ~> 1.0.9
### Installing

This module should be called by a terraform environment configuration via github
```  
      source           = "git@github.com:sce81/terraform-module-aws-vpc.git"
```
or Terraform Cloud
```
      source           = "app.terraform.io/HashiCorp_AWS_Org/aws-vpc/module"
      version          = "1.0.0"
```



##### Usage

    module "aws_vpc" {

        source = "git@github.com:sce81/terraform-module-aws-vpc.git"
        name                    = "primary"
        env                     = var.env
        vpc_cidr                = "10.0.0.0/20"
        public_subnet_cidr      = ["10.0.0.0/24","10.0.1.0/24", "10.0.2.0/24"]
        private_subnet_cidr     = ["10.0.3.0/24","10.0.4.0/24", "10.0.5.0/24"]
        database_subnet_cidr    = ["10.0.6.0/24","10.0.7.0/24", "10.0.8.0/24"]
    }


addional tags can be appended using the following map values

        extra_tags
        public_extra_tags
        private_extra_tags
        database_extra_tags

### Outputs

The following values are outputted

        aws_vpc.main.id
        aws_subnet.public.*.id
        aws_subnet.private.*.id
        aws_subnet.database.*.id

<!-- BEGIN_TF_DOCS -->
## Requirements

No requirements.

## Providers

| Name | Version |
| ---- | ------- |
| <a name="provider_aws"></a> [aws](#provider\_aws) | n/a |

## Modules

No modules.

## Resources

| Name | Type |
| ---- | ---- |
| [aws_default_security_group.main](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/default_security_group) | resource |
| [aws_subnet.database](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/subnet) | resource |
| [aws_subnet.private](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/subnet) | resource |
| [aws_subnet.public](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/subnet) | resource |
| [aws_vpc.main](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/vpc) | resource |
| [aws_availability_zones.available](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/availability_zones) | data source |

## Inputs

| Name | Description | Type | Default | Required |
| ---- | ----------- | ---- | ------- | :------: |
| <a name="input_database_extra_tags"></a> [database\_extra\_tags](#input\_database\_extra\_tags) | Placeholder to allow for additional custom tags to be passed into the module from the environment in map format | `map(any)` | `{}` | no |
| <a name="input_database_subnet_cidr"></a> [database\_subnet\_cidr](#input\_database\_subnet\_cidr) | n/a | `list(any)` | `[]` | no |
| <a name="input_enable_dns_hostnames"></a> [enable\_dns\_hostnames](#input\_enable\_dns\_hostnames) | n/a | `bool` | `true` | no |
| <a name="input_enable_dns_support"></a> [enable\_dns\_support](#input\_enable\_dns\_support) | n/a | `bool` | `true` | no |
| <a name="input_env"></a> [env](#input\_env) | Friendly Env value for the VPC and Subnetwork components | `string` | n/a | yes |
| <a name="input_extra_tags"></a> [extra\_tags](#input\_extra\_tags) | Placeholder to allow for additional custom tags to be passed into the module from the environment in map format | `map(any)` | `{}` | no |
| <a name="input_name"></a> [name](#input\_name) | Friendly Name value for the VPC and Subnetwork components | `string` | n/a | yes |
| <a name="input_private_extra_tags"></a> [private\_extra\_tags](#input\_private\_extra\_tags) | Placeholder to allow for additional custom tags to be passed into the module from the environment in map format | `map(any)` | `{}` | no |
| <a name="input_private_subnet_cidr"></a> [private\_subnet\_cidr](#input\_private\_subnet\_cidr) | n/a | `list(any)` | `[]` | no |
| <a name="input_public_extra_tags"></a> [public\_extra\_tags](#input\_public\_extra\_tags) | Placeholder to allow for additional custom tags to be passed into the module from the environment in map format | `map(any)` | `{}` | no |
| <a name="input_public_subnet_cidr"></a> [public\_subnet\_cidr](#input\_public\_subnet\_cidr) | n/a | `list(any)` | `[]` | no |
| <a name="input_vpc_cidr"></a> [vpc\_cidr](#input\_vpc\_cidr) | n/a | `any` | n/a | yes |

## Outputs

| Name | Description |
| ---- | ----------- |
| <a name="output_database_subnet_ids"></a> [database\_subnet\_ids](#output\_database\_subnet\_ids) | n/a |
| <a name="output_private_subnet_ids"></a> [private\_subnet\_ids](#output\_private\_subnet\_ids) | n/a |
| <a name="output_public_subnet_ids"></a> [public\_subnet\_ids](#output\_public\_subnet\_ids) | n/a |
| <a name="output_vpc_id"></a> [vpc\_id](#output\_vpc\_id) | n/a |
<!-- END_TF_DOCS -->
