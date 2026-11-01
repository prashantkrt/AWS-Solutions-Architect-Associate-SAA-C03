# Encryption and secrets

Encryption protects confidentiality, but access control and key management determine who can use encrypted data.

| Need | Design direction |
|---|---|
| Managed encryption with minimal key administration | AWS-managed service keys where the service supports them |
| Control key policy, grants, or rotation settings | Customer-managed AWS KMS key |
| Store and rotate database/API credentials | Secrets Manager when managed rotation is useful |
| Store configuration values and some secrets | Systems Manager Parameter Store; compare advanced features and cost |
| Protect network traffic | TLS between clients/services, with certificates managed appropriately |

KMS key policies and IAM policies both matter for customer-managed keys. Losing access to a key can make encrypted data unusable; deleting or scheduling deletion of a key has serious consequences. Scope key permissions, audit use, and plan key lifecycle before implementation.

Encryption at rest does not replace TLS, authorization, backups, or data retention controls. Avoid hard-coding secrets in application source, container images, or shell history.
