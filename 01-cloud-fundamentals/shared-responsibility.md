# Shared responsibility model

AWS is responsible for security **of** the cloud; customers are responsible for security **in** the cloud. The division depends on the service and deployment model.

| Area | AWS generally manages | Customer generally manages |
|---|---|---|
| AWS Regions, AZs, and physical facilities | Data centers, physical access, and foundational infrastructure | Selecting Regions and designing workload resilience across them |
| Amazon EC2 | Physical host and virtualization layer | Guest OS, patching, installed software, data, and security group rules |
| Amazon S3 | Service infrastructure and durability mechanisms | Bucket/object access policies, data classification, retention, and encryption choices |
| Managed database | Underlying service platform and many maintenance tasks | Data, users/permissions, configuration choices, backups/retention settings, and application behavior |

Do not treat “managed” as “secure by default for every use.” A public bucket policy, over-permissive role, or exposed database can still be a customer configuration issue.

## Architecture checklist

1. Identify who patches each layer.
2. Identify who controls access to the data and keys.
3. Decide which logs and audit records the workload needs.
4. Confirm backup, retention, and recovery responsibilities.
5. Revisit the boundary when replacing EC2 with a more managed service.

## Exam cue

If a scenario asks who patches the EC2 guest operating system, that is the customer. If it asks who secures the underlying physical AWS data center, that is AWS.
