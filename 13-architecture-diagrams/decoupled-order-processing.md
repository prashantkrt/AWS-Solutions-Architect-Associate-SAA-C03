# Decoupled order processing

```mermaid
flowchart LR
    Client --> API[API Gateway]
    API --> Order[Order service]
    Order --> DB[(Order database)]
    Order --> Queue[SQS queue]
    Queue --> Payment[Payment worker]
    Queue --> Fulfillment[Fulfillment worker]
    Queue -. failed messages .-> DLQ[Dead-letter queue]
    Payment --> Events[EventBridge]
    Events --> Notify[Notification service]
```

Each consumer can scale and retry independently. Confirm whether each business event should be delivered to every consumer; separate queues subscribed to an SNS topic can provide fan-out. Consumers should tolerate duplicate delivery and use idempotency keys for side effects.
