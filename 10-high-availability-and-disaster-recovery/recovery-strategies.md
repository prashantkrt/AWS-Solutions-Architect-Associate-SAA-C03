# Disaster recovery strategy comparison

| Strategy | Standby state | Recovery speed | Relative cost/complexity |
|---|---|---|---|
| Backup and restore | Backups only | Usually slowest | Lowest idle footprint; restore capacity and data movement take time |
| Pilot light | Core data/services available | Faster than restore-only | Moderate; remaining stack must be provisioned and tested |
| Warm standby | Reduced but functioning stack | Faster; scale up to full capacity | Higher ongoing cost and operational work |
| Multi-site active/active | Multiple sites serve traffic | Fastest potential recovery | Highest complexity, consistency challenges, and cost |

Choose from business RTO/RPO, data consistency, regulatory requirements, dependencies, and budget. These labels are patterns, not precise guarantees. Recovery time includes detection, decision, scaling, routing, validation, and communication—not merely instance startup.

## Exercise a recovery plan

Document trigger and owner, data restoration sequence, dependencies, traffic switch, validation criteria, rollback, and communications. Run tests that match the recovery objectives and measure actual RTO/RPO.
