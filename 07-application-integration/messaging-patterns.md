# Messaging and event patterns

## Queue vs. pub/sub vs. event bus

- **Queue (SQS):** A consumer receives a message and deletes it after successful processing. Visibility timeout and retries support recovery; standard queues can deliver duplicates, so consumers should be idempotent.
- **Pub/sub (SNS):** A publisher sends one notification to multiple subscribers. SNS-to-SQS fan-out lets each consumer process independently.
- **Event bus (EventBridge):** Producers publish events; rules route matching events to targets. Useful for event-driven integration across services and accounts.
- **Workflow (Step Functions):** Orchestrates a sequence with state, branching, and retry/catch behavior.

Use a dead-letter queue or failure destination where appropriate, monitor backlog/age, and plan replay. Set visibility timeout long enough for expected processing while preventing prolonged message hiding after worker failure.

### Scenario: bursty image processing

An upload event can enqueue a job; a worker fleet or function consumes jobs at a controlled rate. The queue absorbs bursts, but storage, concurrency, and downstream quotas still need protection. A dead-letter path isolates repeated failures for investigation.
