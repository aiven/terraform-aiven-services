# Service User Data Source

The Service User data source provides information about the existing Aiven Service User.

## Example Usage

```hcl
data "aiven_service_user" "myserviceuser" {
  project = aiven_project.myproject.project
  service_name = aiven_service.myservice.service_name
  username = "<USERNAME>"
}
```

~> **Note** The service user data source is not supported for Aiven Grafana services.

## Argument Reference

* `project` and `service_name` - (Required) define the project and service the user belongs to. They should be defined
  using reference as shown above to set up dependencies correctly.

* `username` - (Required) is the actual name of the user account.

## Attribute Reference

Service users have several computed properties that cannot be set, only read:

* `redis_acl_categories` - Redis specific field, defines command category rules.

* `redis_acl_commands` - Redis specific field, defines rules for individual commands.

* `redis_acl_keys` - Redis specific field, defines key access rules.

* `password` - is the password of the user (not applicable for all services).

* `access_cert` - is the access certificate of the user (not applicable for all services).

* `access_key` - is the access key of the user (not applicable for all services).

* `type` - tells whether the user is primary account or regular account.

Aiven ID format when importing existing resource: `<project_name>/<service_name>/<username>`