---
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "opslevel_service Resource - terraform-provider-opslevel"
subcategory: ""
description: |-
  Manages a service
---

# opslevel_service (Resource)

Manages a service

## Example Usage

```terraform
data "opslevel_lifecycle" "beta" {
    filter {
        field = "alias"
        value = "beta"
    }
}

data "opslevel_tier" "tier3" {
    filter {
        field = "index"
        value = "3"
    }
}

resource "opslevel_team" "foo" {
  name = "foo"
  manager_email = "john.doe@example.com"
  responsibilities = "Responsible for foo frontend and backend"
}

resource "opslevel_service" "foo" {
  name = "foo"

  description = "foo service"
  framework   = "rails"
  language    = "ruby"

  lifecycle_alias = data.opslevel_lifecycle.beta.alias
  tier_alias = data.opslevel_tier.tier3.alias
  owner_alias = opslevel_team.foo.alias
}

output "foo_aliases" {
  value = opslevel_service.example.aliases
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- **name** (String) The display name of the service.

### Optional

- **description** (String) A brief description of the service.
- **framework** (String) The primary software development framework that the service uses.
- **id** (String) The ID of this resource.
- **language** (String) The primary programming language that the service is written in.
- **last_updated** (String)
- **lifecycle_alias** (String) The lifecycle stage of the service.
- **owner_alias** (String) The team that owns the service.
- **product** (String) A product is an application that your end user interacts with. Multiple services can work together to power a single product.
- **tags** (List of String) A list of tags applied to the service.
- **tier_alias** (String) The software tier that the service belongs to.

### Read-Only

- **aliases** (List of String) A list of human-friendly, unique identifiers for the service

## Import

Import is supported using the following syntax:

```shell
terraform import opslevel_service.example Z2lkOi8vb3BzbGV2ZWwvU2VydmljZS82MDI0
```