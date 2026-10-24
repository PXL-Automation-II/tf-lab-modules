# tf-lab-modules

Reusable modules for the PXL [Terraform modules workshop](https://pxl-automation-ii.github.io/terraform-course/#/52-modules-workshop-en).

- `services/webserver-cluster`: a load balancer, an Auto Scaling Group and their security groups.
- `data-storage/mysql`: a MySQL database in RDS.

Versions:

- `v0.1.0`: both modules, as built in the workshop.

Use a module with a Git URL and a tag:

```hcl
module "webserver_cluster" {
  source = "github.com/PXL-Automation-II/tf-lab-modules//services/webserver-cluster?ref=v0.1.0"
  # (inputs)
}
```

The tags `v0.0.1` to `v0.0.4` belong to an earlier version of the workshop. `v0.0.1` and `v0.0.2` use a launch configuration, which AWS no longer allows in accounts created on or after 1 October 2024. A published tag is never changed: a fix becomes a new version.
