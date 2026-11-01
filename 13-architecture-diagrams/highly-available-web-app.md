# Highly available web application

```mermaid
flowchart TD
    U[Users] --> R53[Route 53]
    R53 --> CF[CloudFront]
    CF --> ALB[Application Load Balancer]
    subgraph Region
      subgraph AZ_A[Availability Zone A]
        ALB --> AppA[App instances]
      end
      subgraph AZ_B[Availability Zone B]
        ALB --> AppB[App instances]
      end
      AppA --> DB[(Multi-AZ relational database)]
      AppB --> DB
      AppA --> S3[(Amazon S3 objects)]
      AppB --> S3
    end
```

**Trade-offs:** Multi-AZ application capacity and database failover improve regional availability within one Region. CloudFront can cache eligible content near users. A Multi-AZ database is not a regional DR strategy; separately define backup and cross-Region recovery if required.
