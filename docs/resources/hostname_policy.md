---
page_title: "morpheus_hostname_policy Resource - terraform-provider-morpheus"
subcategory: ""
description: |-
  Provides a Morpheus cluster resource name policy resource
---

# morpheus_hostname_policy

Provides a Morpheus cluster resource name policy resource

## Example Usage

Creating the policy with a global scope:

```terraform
resource "morpheus_hostname_policy" "tf_example_hostname_policy_global" {
  name             = "tf_example_hostname_policy_global"
  description      = "terraform example global hostname policy"
  enabled          = true
  enforcement_type = "fixed"
  naming_pattern   = "$${userInitials.toLowerCase()}dm$${type.take(3).toLowerCase()}$${sequence+1000}"
  scope            = "global"
}
```

Creating the policy with a cloud scope:

```terraform
resource "morpheus_hostname_policy" "tf_example_hostname_policy_cloud" {
  name             = "tf_example_hostname_policy_cloud"
  description      = "terraform example cloud hostname policy"
  enabled          = true
  enforcement_type = "fixed"
  naming_pattern   = "$${userInitials.toLowerCase()}dm$${type.take(3).toLowerCase()}$${sequence+1000}"
  scope            = "cloud"
  cloud_id         = 1
}
```

Creating the policy with a group scope:

```terraform
resource "morpheus_hostname_policy" "tf_example_hostname_policy_group" {
  name             = "tf_example_hostname_policy_group"
  description      = "terraform example group hostname policy"
  enabled          = true
  enforcement_type = "fixed"
  naming_pattern   = "$${userInitials.toLowerCase()}dm$${type.take(3).toLowerCase()}$${sequence+1000}"
  scope            = "group"
  group_id         = 1
}
```

Creating the policy with a role scope:

```terraform
resource "morpheus_hostname_policy" "tf_example_hostname_policy_role" {
  name             = "tf_example_hostname_policy_role"
  description      = "terraform example role hostname policy"
  enabled          = true
  enforcement_type = "fixed"
  naming_pattern   = "$${userInitials.toLowerCase()}dm$${type.take(3).toLowerCase()}$${sequence+1000}"
  scope            = "role"
  role_id          = 1
  apply_each_user  = true
}
```

Creating the policy with a user scope:

```terraform
resource "morpheus_hostname_policy" "tf_example_hostname_policy_user" {
  name             = "tf_example_hostname_policy_user"
  description      = "terraform example user hostname policy"
  enabled          = true
  enforcement_type = "fixed"
  naming_pattern   = "$${userInitials.toLowerCase()}dm$${type.take(3).toLowerCase()}$${sequence+1000}"
  scope            = "user"
  user_id          = 1
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `enforcement_type` (String) The policy enforcement type (fixed or user)
- `name` (String) The name of the hostname naming policy
- `naming_pattern` (String) The hostname naming pattern
- `scope` (String) The filter or scope that the policy is applied to (global, group, cloud, user, role)

### Optional

- `apply_to_each_user` (Boolean) Whether to assign the policy at the individual user level to all users assigned the associated role
- `cloud_id` (Number) The id of the cloud associated with the cloud scoped filter
- `description` (String) The description of the hostname naming policy
- `enabled` (Boolean) Whether the policy is enabled
- `group_id` (Number) The id of the group associated with the group scoped filter
- `role_id` (Number) The id of the role associated with the role scoped filter
- `user_id` (Number) The id of the user associated with the user scoped filter

### Read-Only

- `id` (String) The ID of the hostname naming policy

## Import

Import is supported using the following syntax:

```shell
terraform import morpheus_hostname_policy.tf_example_hostname_policy 1
```