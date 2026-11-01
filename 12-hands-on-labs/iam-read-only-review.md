# Lab · Read-only IAM and account review

**Goal:** Learn which AWS account and role your CLI profile uses without changing resources.

1. Confirm you have explicit permission to use the account. Use an approved sandbox and temporary credentials.
2. Run the identity command in [AWS CLI basics](../01-cloud-fundamentals/aws-cli-basics.md).
3. Record only the role type and whether the account is the expected sandbox; do not commit account IDs, ARNs, or personal identifiers.
4. In the console, inspect the active role's attached permissions in read-only mode if your organization permits it.
5. Explain the difference between the role trust policy and its permissions policy.
6. Sketch a least-privilege policy for a hypothetical read-only S3 listing task; do not apply it to a real role.
7. End by signing out and removing any temporary local credentials according to your organization's process.

**Expected result:** You can identify the principal, reason about least privilege, and explain why an SCP or boundary does not grant permissions.
