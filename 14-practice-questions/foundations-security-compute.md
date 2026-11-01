# Practice · Foundations, security, and compute

Questions are original study exercises. Choose one answer and explain why the alternatives do not satisfy the constraint.

### 1. EC2 guest maintenance

A company runs a licensed application that requires host-level OS configuration on virtual machines. Which option best preserves that control?

A. AWS Lambda · B. Amazon EC2 · C. Amazon S3 · D. Amazon EventBridge

**Answer: B.** EC2 provides guest OS control. Lambda is managed execution, S3 is object storage, and EventBridge routes events.

### 2. Workforce access

Employees need temporary access to several AWS accounts using their corporate identity provider. Which approach is preferred over issuing each employee long-lived IAM access keys?

A. IAM Identity Center with federation · B. Shared root credentials · C. An access key in a shared file · D. Public resource policies

**Answer: A.** Federated workforce access and role-based account assignments provide centralized access with temporary credentials. The other choices increase credential and access risk.

### 3. Shared responsibility

Who is generally responsible for patching the guest operating system on an Amazon EC2 instance?

A. AWS · B. Customer · C. The internet gateway · D. CloudTrail

**Answer: B.** AWS secures the underlying cloud infrastructure; the customer manages the EC2 guest OS.

### 4. Bursty web fleet

A stateless web tier needs to replace unhealthy instances and distribute incoming HTTP requests across two AZs. Which pairing is most appropriate?

A. Auto Scaling group and ALB · B. S3 lifecycle and Glacier · C. CloudTrail and Config · D. EBS snapshots and Direct Connect

**Answer: A.** Auto Scaling maintains/adjusts instance capacity and an ALB routes application traffic. Multi-AZ placement and health checks are important.
