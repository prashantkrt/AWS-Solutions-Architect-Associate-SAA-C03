# Database selection

1. **Start with the model:** relational transactions, key-value/document lookups, in-memory cache, or analytics warehouse?
2. **List access patterns:** query keys, joins, reads/writes, consistency, latency, and growth.
3. **Set operational needs:** patching, backups, failover, scaling, and migration requirements.
4. **Compare recovery and cost:** replicas, storage, I/O, data transfer, and licensing can matter as much as instance price.

### Example: product catalog

If the catalog is relational, requires SQL joins, and has predictable moderate scale, RDS/Aurora may fit. If access is primarily by a known product identifier and extremely low-latency scale is central, a DynamoDB model may fit. If product images are involved, keep binary assets in S3 and store object references/metadata in the database.

### Example: read-heavy web service

First use appropriate database indexes and read replicas or a suitable DynamoDB capacity strategy. Add ElastiCache when repeated reads benefit from a cache and the application can tolerate misses/staleness. A cache alone does not ensure durable data or strong consistency.
