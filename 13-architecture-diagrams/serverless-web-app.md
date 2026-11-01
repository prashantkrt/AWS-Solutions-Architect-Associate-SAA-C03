# Serverless web application

```mermaid
flowchart LR
    User[Client] --> CF[CloudFront]
    CF --> API[API Gateway]
    API --> Fn[Lambda]
    Fn --> DDB[(DynamoDB)]
    Fn --> S3[(S3)]
    Fn --> Q[SQS]
    Q --> Worker[Async worker]
    Worker --> DDB
    Fn --> CW[CloudWatch]
    Worker --> CW
```

**Trade-offs:** This design reduces server management and separates asynchronous processing. Add authentication, scoped execution roles, idempotency, throttling, dead-letter handling, and alarms. Assess concurrency, quotas, data consistency, and per-request costs before selecting it.
