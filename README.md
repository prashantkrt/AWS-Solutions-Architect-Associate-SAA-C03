# AWS Certified Solutions Architect – Associate (SAA-C03)

A structured, practical study guide for designing secure, resilient, high-performing, and cost-aware solutions on AWS. This repository follows the SAA-C03 exam domains and favors service-selection decisions over memorizing product lists.

## Learning roadmap

Follow these 14 course modules in order. The linked guides are the study material; this roadmap groups them into the course sequence and calls out the topics to cover.

| Module | Topics |
|---|---|
| 1. [AWS Global Infrastructure](01-cloud-fundamentals/global-infrastructure.md) | Data centers, Regions, Availability Zones (AZs), Local Zones, Wavelength Zones, edge locations, Outposts, and AWS WAF (introduced here; studied further in Module 12). |
| 2. [Securing AWS Accounts and Resources](02-iam-and-security/README.md) | IAM users, groups, roles, and policies; least privilege; AWS Organizations and service control policies; encryption and secrets. |
| 3. [AWS Basic Networking Concepts](06-networking-and-content-delivery/README.md) | IP addressing and CIDR; VPCs and subnets; public/private routing; internet and NAT gateways; route tables; security groups and network ACLs. |
| 4. [Compute in the Cloud](03-compute-services/README.md) | EC2 instance families and types, pricing options, attached storage, Auto Scaling fundamentals, and AWS Lambda. |
| 5. [AWS Storage and Types](04-storage-services/README.md) | Block, object, and file storage; EBS, S3, EFS, and FSx; storage classes, hybrid storage, and data migration. |
| 6. [AWS Database Services and Types](05-database-services/README.md) | Relational and non-relational databases, caching, analytics, backups, and database migration. |
| 7. [Monitoring AWS Infrastructure and Scaling](08-monitoring-and-management/README.md) | CloudWatch metrics, logs, and alarms; CloudTrail; load balancing; and Auto Scaling. |
| 8. [Automating Infrastructure and Application Creation](03-compute-services/README.md) | Infrastructure as code with AWS CloudFormation and managed application deployment with Elastic Beanstalk. |
| 9. [Microservices in AWS (Containers)](03-compute-services/README.md) | Container fundamentals; Amazon ECS, Amazon EKS, and AWS Fargate. |
| 10. [AWS Advanced Networking](06-networking-and-content-delivery/README.md) | VPC endpoints, VPC peering, Transit Gateway, Site-to-Site VPN, and Direct Connect. |
| 11. [AWS Serverless Portfolio](07-application-integration/README.md) | Amazon SQS, Amazon SNS, Amazon Kinesis, API Gateway, Step Functions, Lambda, and event-driven design. |
| 12. [AWS Edge and Hybrid Services](01-cloud-fundamentals/global-infrastructure.md) | Route 53, CloudFront, AWS WAF, AWS Shield, Firewall Manager, and Outposts. |
| 13. [AWS Disaster Recovery](10-high-availability-and-disaster-recovery/README.md) | Backup plans, restore testing, RTO/RPO, and recovery strategies from backup-and-restore through multi-site. |
| 14. [SAA-C03 Exam Preparation](15-exam-revision/README.md) | Exam-domain mapping, service comparisons, practice questions, and a final review checklist. |

### Additional study resources

- [Hands-on labs](12-hands-on-labs/README.md) — guided, non-deploying exercises and safe console walkthroughs.
- [Architecture diagrams](13-architecture-diagrams/README.md) — Mermaid reference designs and decision flows.
- [Practice questions](14-practice-questions/README.md) — original scenario questions with answer reasoning.
- [Cost optimization](11-cost-optimization/README.md) — pricing models, rightsizing, and cost governance.

### Suggested study sequence

Follow Modules 1–14, using the additional study resources to reinforce each topic. Study security alongside service design, and practice explaining why alternatives do not satisfy the scenario constraints. Finish with the revision sheets and timed question sets.

## Exam domains

The SAA-C03 blueprint groups questions into four domains: Design Secure Architectures, Design Resilient Architectures, Design High-Performing Architectures, and Design Cost-Optimized Architectures. See [exam-domain mapping](15-exam-revision/exam-domain-map.md) for a study crosswalk. Verify current exam details with the [official AWS certification page](https://aws.amazon.com/certification/certified-solutions-architect-associate/).

## Progress tracker

Mark a section complete only after you can explain its key choices without relying on notes.

| Topic | Read | Practice questions | Confidence (1–5) |
|---|:---:|:---:|:---:|
| Cloud fundamentals | [ ] | [ ] | — |
| IAM and security | [ ] | [ ] | — |
| Basic networking | [ ] | [ ] | — |
| Compute services | [ ] | [ ] | — |
| Storage services | [ ] | [ ] | — |
| Database services | [ ] | [ ] | — |
| Monitoring and scaling | [ ] | [ ] | — |
| Infrastructure automation | [ ] | [ ] | — |
| Containers and microservices | [ ] | [ ] | — |
| Advanced networking and edge services | [ ] | [ ] | — |
| Serverless and application integration | [ ] | [ ] | — |
| Disaster recovery | [ ] | [ ] | — |
| SAA-C03 exam preparation | [ ] | [ ] | — |
| Hands-on labs | [ ] | [ ] | — |

## Using this repository

- Each topic README introduces the domain and links to focused service or concept notes.
- Mermaid diagrams are source-controlled text; preview them in a GitHub Markdown renderer.
- CLI snippets are for inspection unless explicitly described otherwise. No lab deploys infrastructure by default.
- AWS pricing, service features, and exam content can change. Confirm time-sensitive details in current AWS documentation before acting.
- Never paste account identifiers, credentials, personal data, or sensitive workload information into shared notes.

## Contributions

Keep explanations decision-oriented, link related topics instead of duplicating them, and include the trade-off behind each recommendation. Use original practice questions rather than reproducing copyrighted exam material.
