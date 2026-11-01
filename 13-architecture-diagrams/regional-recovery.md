# Regional recovery pattern

```mermaid
flowchart LR
    Users --> DNS[Route 53]
    DNS --> Primary[Primary Region]
    Primary --> Data1[(Primary data)]
    Primary -. replication / backups .-> Recovery[Recovery Region]
    Recovery --> Data2[(Replica or restored data)]
    Recovery -. activate and validate .-> DNS
```

The recovery Region can be backup-only, pilot light, warm standby, or active/active. DNS routing does not itself replicate data or validate application health. Define ownership, data consistency, promotion, failback, and testing procedures.
