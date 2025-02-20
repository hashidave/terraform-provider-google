---
# ----------------------------------------------------------------------------
#
#     ***     AUTO GENERATED CODE    ***    Type: MMv1     ***
#
# ----------------------------------------------------------------------------
#
#     This file is automatically generated by Magic Modules and manual
#     changes will be clobbered when the file is regenerated.
#
#     Please read more about how to change this file in
#     .github/CONTRIBUTING.md.
#
# ----------------------------------------------------------------------------
subcategory: "Resource Manager"
page_title: "Google: google_resource_manager_lien"
description: |-
  A Lien represents an encumbrance on the actions that can be performed on a resource.
---

# google\_resource\_manager\_lien

A Lien represents an encumbrance on the actions that can be performed on a resource.



## Example Usage - Resource Manager Lien


```hcl
resource "google_resource_manager_lien" "lien" {
  parent       = "projects/${google_project.project.number}"
  restrictions = ["resourcemanager.projects.delete"]
  origin       = "machine-readable-explanation"
  reason       = "This project is an important environment"
}

resource "google_project" "project" {
  project_id = "staging-project"
  name       = "A very important project!"
}
```

## Argument Reference

The following arguments are supported:


* `reason` -
  (Required)
  Concise user-visible strings indicating why an action cannot be performed
  on a resource. Maximum length of 200 characters.

* `origin` -
  (Required)
  A stable, user-visible/meaningful string identifying the origin
  of the Lien, intended to be inspected programmatically. Maximum length of
  200 characters.

* `parent` -
  (Required)
  A reference to the resource this Lien is attached to.
  The server will validate the parent against those for which Liens are supported.
  Since a variety of objects can have Liens against them, you must provide the type
  prefix (e.g. "projects/my-project-name").

* `restrictions` -
  (Required)
  The types of operations which should be blocked as a result of this Lien.
  Each value should correspond to an IAM permission. The server will validate
  the permissions against those for which Liens are supported.  An empty
  list is meaningless and will be rejected.
  e.g. ['resourcemanager.projects.delete']


- - -



## Attributes Reference

In addition to the arguments listed above, the following computed attributes are exported:

* `id` - an identifier for the resource with format `{{name}}`

* `name` -
  A system-generated unique identifier for this Lien.

* `create_time` -
  Time of creation


## Timeouts

This resource provides the following
[Timeouts](/docs/configuration/resources.html#timeouts) configuration options:

- `create` - Default is 20 minutes.
- `delete` - Default is 20 minutes.

## Import


Lien can be imported using any of these accepted formats:

```
$ terraform import google_resource_manager_lien.default {{parent}}/{{name}}
```
