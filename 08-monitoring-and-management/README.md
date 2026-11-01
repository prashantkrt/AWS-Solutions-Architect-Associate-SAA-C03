# 08 · Monitoring and management

Observability and governance help detect faults, understand changes, and operate consistently across accounts.

| Service | Primary role |
|---|---|
| Amazon CloudWatch | Metrics, logs, alarms, dashboards, and operational signals |
| AWS CloudTrail | Record account/API activity for audit and investigation |
| AWS Config | Track resource configuration and evaluate rules |
| AWS Systems Manager | Fleet operations, parameter storage, and automation capabilities |
| AWS Organizations / Control Tower | Account governance and multi-account foundations |
| AWS Trusted Advisor | Recommendations across selected cost, security, reliability, and performance areas |

CloudWatch answers “what is the system doing?”; CloudTrail helps answer “which API action occurred, by whom, and when?” Configure retention and access intentionally; logs and metrics can incur charges.

Read [monitoring and audit signals](monitoring-and-audit.md). For CLI-only observation, use the commands in [cloud fundamentals](../01-cloud-fundamentals/aws-cli-basics.md).
