# tf-lab-modules

Reusable modules for the PXL [Terraform modules workshop](https://pxl-automation-ii.github.io/terraform-course/#/52-modules-workshop-en) and [Terragrunt workshop](https://pxl-automation-ii.github.io/terraform-course/#/57-terragrunt-workshop).

- `services/webserver-cluster`: a load balancer, an Auto Scaling Group and their security groups.
- `services/asg-schedule`: two scheduled actions that scale an Auto Scaling Group up at 9:00 and down at 17:00. From `v1.0.0`.
- `data-storage/mysql`: a MySQL database in RDS.

Versions:

- `v0.1.0`: `webserver-cluster` and `mysql`, as built in the modules workshop.
- `v0.2.0`: `webserver-cluster` gets the optional input `server_text`, the text on the web page.
- `v1.0.0`: for the Terragrunt workshop. `webserver-cluster` takes the inputs `db_address` and `db_port` instead of reading the database state, and `asg-schedule` is new. Callers of `v0.2.0` must change their inputs, so this is a major version.
- `v0.1.1`, `v0.2.1` and `v1.0.1`: patch releases of the three versions above. `webserver-cluster` looks up the newest Ubuntu 24.04 image with a `data "aws_ami"` block instead of a hard-coded AMI ID. Use these.

Use a module with a Git URL and a tag:

```hcl
module "webserver_cluster" {
  source = "github.com/PXL-Automation-II/tf-lab-modules//services/webserver-cluster?ref=v0.2.1"
  # (inputs)
}
```

The tags `v0.0.1` to `v0.0.4` belong to an earlier version of the workshop. `v0.0.1` and `v0.0.2` use a launch configuration, which AWS no longer allows in accounts created on or after 1 October 2024. A published tag is never changed: a fix becomes a new version.
