# Agent instructions

## OCI Compute launches

Before any agent launches an OCI Compute instance through Terraform/OpenTofu, OCI CLI, an SDK, an API, or another tool, require the effective launch request to set `instanceOptions.areLegacyImdsEndpointsDisabled=true` (`instance_options.are_legacy_imds_endpoints_disabled = true` in Terraform). OCI permits IMDSv1 by default. Check the evaluated plan or request, including modules and pinned submodule revisions, and fail closed if the value is absent, false, or unknown. Do not apply the plan or retry through a different tool to bypass this check. A tenancy-wide OCI IAM restriction is the required enforcement boundary; this instruction is an additional agent-side check.
