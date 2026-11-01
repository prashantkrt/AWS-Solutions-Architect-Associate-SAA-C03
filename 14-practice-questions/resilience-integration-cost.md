# Practice · Resilience, integration, and cost

### 1. Absorb asynchronous bursts

A backend worker is temporarily slower than its producer. Which service most directly buffers work for later consumption?

A. SQS · B. Route 53 · C. KMS · D. CloudFront

**Answer: A.** SQS decouples producer and consumer rates. Configure visibility, retries, idempotency, and a dead-letter strategy.

### 2. Recovery targets

A workload must recover quickly after a Region-wide outage, but full duplicate capacity is too expensive. Which input should drive the recovery design choice?

A. RTO and RPO · B. VPC CIDR alone · C. Instance family name · D. Number of IAM users

**Answer: A.** RTO/RPO and business constraints determine whether backup/restore, pilot light, or warm standby is appropriate.

### 3. Interruptible batch work

A batch workload can checkpoint and retry after interruption. Which compute pricing option should be considered for flexible capacity?

A. Spot Instances · B. Dedicated Hosts only · C. On-premises tape · D. Route 53 Resolver

**Answer: A.** Spot can reduce compute cost for interruptible workloads, with interruption handling designed in.

### 4. API activity investigation

An auditor needs to identify the principal that made an AWS API call and when. Which service is most relevant?

A. CloudTrail · B. CloudWatch dashboard only · C. EFS · D. NAT Gateway

**Answer: A.** CloudTrail records API activity. CloudWatch metrics/logs provide complementary operational signals.
