# 05 · Database services

Select databases by data model, consistency, query patterns, scale, and operational responsibility—not by familiarity alone.

| Service | Model | Typical fit |
|---|---|---|
| Amazon RDS | Managed relational engines | Conventional SQL applications and transactions |
| Amazon Aurora | AWS-managed relational engine compatible with MySQL/PostgreSQL | Relational workloads needing Aurora architecture and scaling options |
| Amazon DynamoDB | Managed key-value/document NoSQL | Low-latency access by known partition/sort keys at scale |
| Amazon ElastiCache | In-memory cache | Reduce repeated database reads or support ephemeral low-latency data |
| Amazon Redshift | Data warehouse | Analytical SQL over large datasets |
| Amazon DocumentDB | Document database service | MongoDB-compatible document workloads |

## Design reminders

- Multi-AZ for RDS is primarily a high-availability/failover pattern, not a read-scaling design. Read replicas address read scaling and can have replication lag.
- DynamoDB access patterns should drive key design; a relational schema cannot simply be copied without considering partition distribution.
- A cache is not the system of record. Plan for misses, eviction, stale values, and cache failure.
- Backups, point-in-time recovery, encryption, and maintenance windows differ by service and configuration.
- **AWS Database Migration Service (AWS DMS)** supports database migration and replication; assess source/target compatibility, conversion needs, and cutover planning.

Read [relational vs. NoSQL](relational-vs-nosql.md) and [RDS, Aurora, and DynamoDB](database-selection.md).
