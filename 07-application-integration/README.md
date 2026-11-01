# 07 · Application integration

Decouple components so that variable workloads and temporary failures do not force every service to operate in lockstep.

| Service | Pattern | Key distinction |
|---|---|---|
| Amazon SQS | Queue | Consumers poll; messages remain until deleted or expire |
| Amazon SNS | Pub/sub notifications | Pushes a message to subscribed endpoints; can fan out to queues |
| Amazon Kinesis | Streaming data | Ingests and processes ordered streams of real-time data; choose a Kinesis service based on the streaming use case |
| Amazon EventBridge | Event bus and rules | Routes events based on event content and source |
| AWS Step Functions | Workflow orchestration | Coordinates steps, retries, branching, and state |
| Amazon API Gateway | Managed API front door | Authentication, throttling, and API integrations |

Design for duplicate delivery where applicable, idempotent consumers, bounded retries, dead-letter handling, and message visibility/retention. A queue smooths bursts but does not make downstream processing unlimited.

See [messaging patterns](messaging-patterns.md) and [decoupled order-processing scenario](../13-architecture-diagrams/decoupled-order-processing.md).
