# SAA-C03 exam-domain map

Use this as a crosswalk between the official exam domains and repository sections. Confirm domain wording and weighting in the current official exam guide before sitting the exam.

| Exam domain | Key design questions | Repository sections |
|---|---|---|
| Design Secure Architectures | Who can access? How is data protected? Where are network and audit boundaries? | [IAM/security](../02-iam-and-security/README.md), [networking](../06-networking-and-content-delivery/README.md), [monitoring](../08-monitoring-and-management/README.md) |
| Design Resilient Architectures | What fails? What are RTO/RPO? How are failures detected and recovered? | [HA/DR](../10-high-availability-and-disaster-recovery/README.md), [storage](../04-storage-services/README.md), [databases](../05-database-services/README.md) |
| Design High-Performing Architectures | What are latency, throughput, scaling, and data-access needs? | [compute](../03-compute-services/README.md), [storage](../04-storage-services/README.md), [databases](../05-database-services/README.md), [networking](../06-networking-and-content-delivery/README.md) |
| Design Cost-Optimized Architectures | Which resources are idle, overprovisioned, or poorly matched to usage? | [cost optimization](../11-cost-optimization/README.md), [compute](../03-compute-services/README.md), [storage](../04-storage-services/README.md) |

Many questions span domains. A low-cost answer that violates availability or security constraints is not the best architecture.
