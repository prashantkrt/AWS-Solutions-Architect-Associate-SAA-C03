# Amazon S3 storage classes and protection

S3 stores objects in buckets. Pick a storage class based on access frequency, latency, retrieval behavior, minimum storage duration, and availability requirements.

| Class family | Typical consideration |
|---|---|
| S3 Standard | Frequently accessed data requiring low-latency access |
| Intelligent-Tiering | Unknown or changing access patterns; monitoring and optional archive tiers have conditions |
| Standard-IA / One Zone-IA | Infrequently accessed data; retrieval charges and availability/resilience differ |
| Glacier Instant/Flexible/Deep Archive | Archive data with retrieval latency ranging from milliseconds to hours |

Exact minimums, retrieval times, fees, and eligibility can change; consult current service pricing before making a decision.

## Protection checklist

- Block public access unless public access is explicitly required.
- Use least-privilege bucket/access-point policies and account-level controls.
- Enable versioning when recovery from overwrite/delete is required; consider MFA delete and retention controls where appropriate.
- Use lifecycle rules for transitions and expiration. Validate that expiration does not conflict with legal retention or recovery.
- Consider replication when another copy or Region is required; replication is not a backup against all deletion/corruption scenarios.
- Select server-side encryption and key ownership based on compliance and access requirements.
