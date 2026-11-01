# Compute selection scenarios

| Scenario clue | Likely direction | Validate |
|---|---|---|
| Existing application needs a specific OS package and host access | EC2 | Patching, AMI maintenance, and capacity |
| Function starts on an event and runs briefly | Lambda | Runtime limits, concurrency, retries, and idempotency |
| Container workload without managing servers | ECS with Fargate | Compatibility and task resource pricing |
| Existing Kubernetes ecosystem is a hard requirement | EKS | Cluster operations and total control-plane/worker costs |
| Need to distribute web requests across targets | ALB or another fit-for-protocol ELB | Protocol, routing, and health-check behavior |
| Interruptible batch jobs can retry | Spot capacity | Checkpointing and interruption tolerance |

Elastic Beanstalk can reduce deployment setup for conventional web applications, while still exposing underlying AWS resources. It is not the same as a fully serverless execution model.

For a real application, compare end-to-end operational responsibility, scaling behavior, compatibility, security, and cost—not just the compute line item.
