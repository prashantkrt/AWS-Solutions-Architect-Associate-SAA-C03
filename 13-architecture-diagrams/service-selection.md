# Service-selection decision flow

```mermaid
flowchart TD
    Start[Describe workload and constraints] --> Data{Primary data model?}
    Data -->|Relational SQL| RDS[RDS or Aurora]
    Data -->|Key-value or document by known key| DDB[DynamoDB]
    Data -->|Shared files| FS[EFS or FSx]
    Data -->|Objects and archives| S3[S3]
    Start --> Compute{Compute control needed?}
    Compute -->|Host or OS control| EC2[EC2]
    Compute -->|Containers| Container[ECS or EKS; consider Fargate]
    Compute -->|Event-driven managed execution| Lambda[Lambda]
    Start --> Failure{Recovery objective?}
    Failure -->|AZ fault| MultiAZ[Multi-AZ design]
    Failure -->|Regional event| DR[Select DR pattern using RTO/RPO]
```

Use this as a prompt, not a service recommender. A complete answer also accounts for security, integration, scaling, operational burden, availability, and total cost.
