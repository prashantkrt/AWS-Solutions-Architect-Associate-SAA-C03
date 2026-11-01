# 10 · High availability and disaster recovery

Resilience is designed around failure modes and business objectives—not a blanket requirement to duplicate everything everywhere.

## Define recovery objectives

- **RTO (Recovery Time Objective):** Maximum acceptable time to restore service.
- **RPO (Recovery Point Objective):** Maximum acceptable data loss measured in time.
- **Backup and restore:** Lowest standby cost; recovery is generally slower.
- **Pilot light:** Keep core data/services ready, scale the rest after failure.
- **Warm standby:** Maintain a reduced but working environment and scale up during recovery.
- **Multi-site active/active:** Serve traffic from multiple sites; highest complexity and often cost.

Use AWS Backup plans to centrally define backup selections, schedules, lifecycle, and retention for supported resources. Multi-AZ handles some AZ failures, but it does not replace backups or regional recovery. Replication is not backup: bad writes/deletions can replicate. Test failover and restore procedures, including DNS and dependencies.

Read [recovery strategy comparison](recovery-strategies.md) and inspect the [regional recovery diagram](../13-architecture-diagrams/regional-recovery.md).
