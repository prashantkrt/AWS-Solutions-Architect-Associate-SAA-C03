# 09 · Serverless architecture

Serverless means AWS manages more of the underlying capacity and availability work; it does not mean there are no limits, costs, or design responsibilities.

## Common pattern

API Gateway can receive requests, Lambda can run application logic, and DynamoDB or S3 can persist data. SQS/EventBridge can separate asynchronous work. Apply least-privilege execution roles, timeouts, retries, idempotency, concurrency limits, and observability.

## Design trade-offs

- Lambda scales with events, but concurrency quotas, cold starts, execution limits, and downstream connection pressure matter.
- DynamoDB can scale without managing database servers, but access patterns and key design are central.
- API Gateway is useful for managed APIs; CloudFront may improve global delivery and edge protection.
- Serverless is not automatically cheaper for steady, high-volume workloads. Compare measured usage and operational cost.

See [serverless design patterns](serverless-patterns.md) and [serverless reference diagram](../13-architecture-diagrams/serverless-web-app.md).
