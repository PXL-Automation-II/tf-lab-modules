# tf-lab-modules

Reusable modules for the PXL [Terraform modules workshop](https://pxl-automation-ii.github.io/terraform-course/#/52-modules-workshop) and [Terragrunt workshop](https://pxl-automation-ii.github.io/terraform-course/#/57-terragrunt-workshop).

| Module | Contents |
| --- | --- |
| `services/webserver-cluster` | A load balancer, an Auto Scaling Group and their security groups. |
| `services/asg-schedule` | Two scheduled actions that scale an Auto Scaling Group up at 9:00 and down at 17:00. From `v1.0.0`. |
| `data-storage/mysql` | A MySQL database in RDS. |

The versions:

| Version | Changes |
| --- | --- |
| `v0.1.0` | `webserver-cluster` and `mysql`, as built in the modules workshop. |
| `v0.2.0` | `webserver-cluster` gets the optional input `server_text`, the text on the web page. |
| `v1.0.0` | For the Terragrunt workshop. `webserver-cluster` takes the inputs `db_address` and `db_port` instead of reading the database state, and `asg-schedule` is new. Callers of `v0.2.0` must change their inputs, so this is a major version. |
| `v0.1.1`, `v0.2.1`, `v1.0.1` | Patch releases of the three versions above. `webserver-cluster` looks up the newest Ubuntu 24.04 image with a `data "aws_ami"` block instead of a hard-coded AMI ID. |
| `v0.1.2`, `v0.2.2`, `v1.0.2` | The next patch releases. `webserver-cluster` puts its instances in the subnets of the Availability Zones that offer its instance type, instead of a fixed list of `us-east-1a` to `us-east-1d`. Zone names map to other data centers in every AWS account, so a fixed list can contain a zone without the instance type. Use these. |

Use a module with a Git URL and a tag:

```hcl
module "webserver_cluster" {
  source = "github.com/PXL-Automation-II/tf-lab-modules//services/webserver-cluster?ref=v0.2.2"
  # (inputs)
}
```

The tags `v0.0.1` to `v0.0.4` belong to an earlier version of the workshop. `v0.0.1` and `v0.0.2` use a launch configuration, which AWS no longer allows in accounts created on or after 1 October 2024. A published tag is never changed: a fix becomes a new version.
