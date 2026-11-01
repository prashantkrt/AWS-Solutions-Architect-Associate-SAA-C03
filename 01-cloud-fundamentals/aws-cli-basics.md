# AWS CLI: read-only orientation

These commands inspect the caller's current identity and configuration. They do not create or modify AWS resources. Install and configure the AWS CLI using current AWS guidance; use a named profile and temporary credentials where possible.

```bash
# Confirm the credentials and account associated with the selected profile
aws sts get-caller-identity --profile study

# List configured profiles and Regions (local configuration only)
aws configure list-profiles
aws configure list --profile study

# List Regions offered to the account
aws ec2 describe-regions --all-regions --profile study \
  --query 'Regions[].{Region:RegionName,Status:OptInStatus}' --output table
```

`--profile study` selects a local credential profile; it does not grant permissions. A denied call may indicate the role lacks permission and is not a reason to broaden access automatically. Avoid putting access keys in shell history or notes.

To inspect a resource, use its service's `describe`/`list` command with the narrowest account, Region, and resource filters available. Review command effects before running: not every AWS CLI operation is read-only.
