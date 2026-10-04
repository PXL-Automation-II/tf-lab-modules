# tf-lab-modules

PXL Terraform module versioning lab, used in the Terraform modules workshop.

Use these versions:

- `v0.0.3`: `webserver-cluster` with a launch template.
- `v0.0.4`: the same module with one extra comment, to practice moving staging to a new version.

`v0.0.1` and `v0.0.2` stay as they were published. They use a launch configuration, which AWS no longer allows in accounts created on or after 1 October 2024. A published tag is never changed: a fix becomes a new version.
