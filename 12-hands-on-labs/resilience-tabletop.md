# Lab · Resilience tabletop exercise

**Goal:** Choose a recovery design for a fictional order service.

1. Set business objectives: for this exercise, assume RTO of 4 hours and RPO of 15 minutes.
2. Draw the primary Region's application, database, queue, and object storage.
3. List single-AZ, AZ-wide, and Region-wide failure scenarios.
4. Compare backup/restore, pilot light, warm standby, and active/active against the objectives.
5. Identify whether database replication or backups meet the RPO and whether replicated deletions are recoverable.
6. Define who declares a disaster, what switches traffic, and how the team validates recovery.
7. Record unresolved assumptions and the tests needed to validate RTO/RPO.

**No resources are created.** The stated objectives are exercise assumptions, not AWS service guarantees.
