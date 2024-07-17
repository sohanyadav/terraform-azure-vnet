# terraform-azure-vnet
# Terraform Azure Infrastructure

This Terraform configuration defines an Azure infrastructure using the Azure provider.

## Table of Contents

- [Introduction](#introduction)
- [Usage](#usage)
- [Module Inputs](#module-inputs)
- [Module Outputs](#module-outputs)
- [Examples](#examples)
- [License](#license)

## Introduction
This repository contains Terraform code to deploy resources on Microsoft Azure, including a resource group and a virtual network.

## Usage
You can use this module in your Terraform configuration like this:

The "vnet" module creates an Azure Virtual Network. It references the resource group created by the "resource_group" module.

# Examples

```hcl
module "vnet" {
  source              = "git::https://github.com/sohanyadav/terraform-azure-vnet.git?ref=v1.0.0"
  name                = "app"
  environment         = "test"
  resource_group_name = module.resource_group.resource_group_name
  location            = module.resource_group.resource_group_location
  address_space       = ["10.0.0.0/16"]
}
```
Please ensure you specify the correct 'source' path for the module.

## Module Inputs
The following input variables can be configured:

- 'name': The name for the resource group and virtual network.
- 'environment': The environment or purpose of the resources.
- 'location': The Azure region where the resources will be created.
- 'address_space': The address space for the virtual network.

## Module Outputs
This module provides the following outputs:

- 'resource_group_name': The name of the created Azure resource group.
- 'resource_group_location': The location of the created Azure resource group.

# Examples
For detailed examples on how to use this module, please refer to the '[example](https://github.com/sohanyadav/terraform-azure-vnet/blob/master/_example)' directory within this repository.

# License
This Terraform module is provided under the '[License Name]' License. Please see the [LICENSE](https://github.com/sohanyadav/terraform-azure-vnet/blob/master/LICENSE) file for more details.

# Author
Your Name
Replace '[License Name]' and '[Your Name]' with the appropriate license and your information. Feel free to expand this README with additional details or usage instructions as needed for your specific use case.

<!-- BEGIN_TF_DOCS -->
## Requirements

| Name | Version |
|------|---------|
| <a name="requirement_terraform"></a> [terraform](#requirement\_terraform) | >= 1.0.0 |
| <a name="requirement_azurerm"></a> [azurerm](#requirement\_azurerm) | >=2.90.0 |

## Providers

| Name | Version |
|------|---------|
| <a name="provider_azurerm"></a> [azurerm](#provider\_azurerm) | >=2.90.0 |

## Modules

| Name | Source | Version |
|------|--------|---------|
| <a name="module_labels"></a> [labels](#module\_labels) | git::https://github.com/sohanyadav/terraform-azure-labels.git | v1.0.0 |

## Resources

| Name | Type |
|------|------|
| [azurerm_network_ddos_protection_plan.ddos](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/network_ddos_protection_plan) | resource |
| [azurerm_network_watcher.flow_log_nw](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/network_watcher) | resource |
| [azurerm_virtual_network.vnet](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/virtual_network) | resource |

## Inputs

+| Name | Description | Type | Default | Required |
+|------|-------------|------|---------|:--------:|
+| <a name="input_create"></a> [create](#input\_create) | Used when creating the Resource Group | `string` | `"30m"` | no |
+| <a name="input_delete"></a> [delete](#input\_delete) | Used when deleting the Resource Group | `string` | `"70m"` | no |
+| <a name="input_enabled"></a> [enabled](#input\_enabled) | Flag to control the module creation | `bool` | `true` | no |
+| <a name="input_environment"></a> [environment](#input\_environment) | Environment (e.g. `prod`, `dev`, `staging`). | `string` | `"-example"` | no |
+| <a name="input_label_order"></a> [label\_order](#input\_label\_order) | Label order, e.g. `name`,`application`. | `list(any)` | <pre>[<br>  "name",<br>  "environment"<br>]</pre> | no |
+| <a name="input_location"></a> [location](#input\_location) | Location where resource should be created | `string` | `"West Europe"` | no |
+| <a name="input_lock_level"></a> [lock\_level](#input\_lock\_level) | n/a | `string` | `"CanNotDelete"` | no |
+| <a name="input_managedby"></a> [managedby](#input\_managedby) | ManagedBy, eg 'sohanyadav'. | `string` | `"example"` | no |
+| <a name="input_name"></a> [name](#input\_name) | The Name which should be used for this Resource Group.Changing this forces a new Resource Group to be created. | `string` | `"resource-group"` | no |
+| <a name="input_read"></a> [read](#input\_read) | Used when retrieving the Resource Group | `string` | `"90m"` | no |
+| <a name="input_repository"></a> [repository](#input\_repository) | Terraform current module repo | `string` | `"https://github.com/sohanyadav/terraform-azure-resource-group"` | no |
+| <a name="input_resource_lock_enabled"></a> [resource\_lock\_enabled](#input\_resource\_lock\_enabled) | enable or disable lock resource | `bool` | `false` | no |
+| <a name="input_update"></a> [update](#input\_update) | Used when updating the Resource Group | `string` | `"50m"` | no |

## Outputs

| Name | Description |
|------|-------------|
| <a name="output_ddos_protection_plan_id"></a> [ddos\_protection\_plan\_id](#output\_ddos\_protection\_plan\_id) | The ID of the DDoS Protection Plan |
| <a name="output_network_watcher_id"></a> [network\_watcher\_id](#output\_network\_watcher\_id) | The ID of the Network Watcher. |
| <a name="output_network_watcher_name"></a> [network\_watcher\_name](#output\_network\_watcher\_name) | The name of Network Watcher deployed. |
| <a name="output_vnet_address_space"></a> [vnet\_address\_space](#output\_vnet\_address\_space) | Concatenated address space of the virtual network |
| <a name="output_vnet_guid"></a> [vnet\_guid](#output\_vnet\_guid) | The GUID of the virtual network. |
| <a name="output_vnet_id"></a> [vnet\_id](#output\_vnet\_id) | The id of the newly created vNet |
| <a name="output_vnet_location"></a> [vnet\_location](#output\_vnet\_location) | The location of the newly created vNet |
| <a name="output_vnet_name"></a> [vnet\_name](#output\_vnet\_name) | The name of the newly created vNet |
| <a name="output_vnet_rg_name"></a> [vnet\_rg\_name](#output\_vnet\_rg\_name) | The name of the resource group in which to create the virtual network. Changing this forces a new resource to be created |
<!-- END_TF_DOCS -->