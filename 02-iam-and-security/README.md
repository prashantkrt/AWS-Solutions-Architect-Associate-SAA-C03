# 02 · IAM and security

Design access controls and data protections around least privilege, explicit ownership, and layered defenses.

## Core concepts

- **IAM users, groups, and roles:** Users represent IAM identities, groups simplify permission assignment to collections of users, and roles provide assumable temporary credentials for people and workloads. Prefer federation and roles over long-lived access keys.
- **Policies:** Identity-based policies grant permissions to identities; resource-based policies attach permissions to resources. An explicit deny overrides an allow. A permissions boundary or organization service control policy limits what can be granted; neither grants permissions by itself.
- **Federation:** Use an identity provider and IAM Identity Center for workforce access. For cross-account access, use roles and tightly scoped trust policies.
- **Encryption:** AWS KMS manages cryptographic keys and policy controls. Encrypt data in transit with TLS and at rest with service-supported encryption; understand who controls keys and who can decrypt.
- **Defense in depth:** Combine identity controls, network boundaries, encryption, logging, patching, and backup protection. A private subnet alone is not a complete security design.

## Selection reminders

| Need | Consider |
|---|---|
| Store and rotate application secrets | Secrets Manager; compare rotation needs and pricing with Systems Manager Parameter Store |
| Centrally govern multiple accounts | AWS Organizations, SCPs, and IAM Identity Center |
| Apply a maximum-permission guardrail to member accounts | An Organizations SCP; it does not grant permissions or affect the management account |
| Audit API activity | CloudTrail |
| Protect keys with managed policy controls | AWS KMS |

See [IAM policy evaluation](iam-policy-evaluation.md) and [encryption and secrets](encryption-and-secrets.md).

## Safe practice

Use the [read-only identity lab](../12-hands-on-labs/iam-read-only-review.md). Do not test permissions by creating access keys or modifying production policies.
