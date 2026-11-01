# Service comparison cheat sheet

| Compare | Choose based on |
|---|---|
| S3 vs EBS vs EFS | Object API vs block device vs shared file system |
| RDS Multi-AZ vs read replica | Availability/failover vs read scaling |
| SQS vs SNS vs EventBridge | Work queue vs pub/sub delivery vs event routing |
| ALB vs NLB | HTTP-aware Layer 7 routing vs Layer 4 network traffic |
| NAT gateway vs VPC endpoint | Outbound internet egress vs private access to supported AWS services |
| Security group vs network ACL | Stateful resource/ENI filtering vs stateless subnet filtering |
| Multi-AZ vs multi-Region | AZ resilience vs regional recovery/latency objectives |
| Secrets Manager vs Parameter Store | Managed secret lifecycle/rotation needs vs parameter/configuration use cases |
| Spot vs On-Demand vs commitment | Interruptible flexibility vs pay-as-you-go vs stable usage commitment |

## Fast scenario cues

- Need shared POSIX-style files across instances → consider EFS/FSx, not S3.
- Need durable object storage with lifecycle tiers → consider S3.
- Need independent consumers and buffering → consider queues; handle duplicates.
- Need compliance/audit trail of API actions → consider CloudTrail.
- Need reduced compute cost for retryable batch → consider Spot.
- Need cross-Region recovery → define data replication/backup and recovery runbooks, not only DNS failover.
