# Final review checklist

## Before practice exams

- [ ] Explain the shared responsibility boundary for EC2, S3, and a managed database.
- [ ] Reason through explicit deny, role trust, identity/resource policies, boundaries, and SCPs.
- [ ] Select among EC2, containers, and Lambda using control and operational constraints.
- [ ] Distinguish S3, EBS, EFS/FSx, and storage lifecycle/retrieval trade-offs.
- [ ] Choose RDS/Aurora, DynamoDB, cache, or warehouse from data access patterns.
- [ ] Trace VPC routes and distinguish security groups, NACLs, NAT, endpoints, and gateways.
- [ ] Explain queue, topic, event bus, and workflow patterns including retries and idempotency.
- [ ] Distinguish CloudWatch, CloudTrail, Config, and Systems Manager roles.
- [ ] Select recovery strategy from RTO/RPO and cost; distinguish replication from backup.
- [ ] Evaluate cost beyond compute: data transfer, requests, retrieval, logging, and idle resources.

## During each scenario

1. Identify the explicit requirement (not an assumed one).
2. Separate hard constraints from preferences.
3. Eliminate options that violate security, protocol, data model, or recovery targets.
4. Prefer the least complex option that meets the stated requirements.
5. Check hidden costs and operational trade-offs.
6. Review why each missed distractor was wrong, then revisit the related topic.
