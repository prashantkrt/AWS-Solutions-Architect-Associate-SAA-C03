# Relational vs. NoSQL

| Question | Relational (RDS/Aurora) | NoSQL (DynamoDB) |
|---|---|---|
| Is SQL and a relational schema central? | Strong fit | Not the primary model |
| Are joins and flexible ad hoc queries important? | Often a fit | Model known access patterns instead |
| Is access predictable by key at very large scale? | Possible, but capacity/architecture matter | Strong fit when partition and key design fit |
| Is transaction behavior required? | Relational transactions | DynamoDB supports transactions with service-specific trade-offs |
| Who manages much of the database platform? | AWS manages service infrastructure; customer still configures and operates data | AWS manages scaling/platform; customer designs keys, access, and capacity settings |

Do not equate NoSQL with “no schema” or relational with “cannot scale.” The right answer is driven by query pattern, consistency, data shape, and operational constraints.

For RDS, Multi-AZ supports availability/failover. Read replicas are used for read scaling and can be eventually consistent due to replication lag. Aurora has its own architecture, feature set, and pricing; compare the exact engine compatibility and workload.
