# Serverless design patterns

## Synchronous request path

API Gateway → Lambda → DynamoDB/S3. Keep the synchronous path bounded; set timeouts, validate requests, and return predictable errors. Put long-running work on an asynchronous path.

## Event-driven processing

S3/EventBridge/SNS can trigger Lambda or publish to SQS. A queue can absorb bursts and isolate producer availability from consumer capacity. Use idempotency, retry policies, dead-letter handling, and concurrency controls.

## Operational guardrails

- Give every function a dedicated least-privilege execution role.
- Store secrets in a managed secret store, not environment values that are treated as harmless.
- Monitor errors, duration, throttles, concurrency, and downstream latency.
- Consider VPC attachment only when private network access is required; it has networking implications and does not inherently secure the function.
- Model requests, duration, memory, data transfer, API usage, and logging when estimating cost.

Serverless can reduce server maintenance, but service quotas, data design, secure permissions, and failure handling remain architectural responsibilities.
