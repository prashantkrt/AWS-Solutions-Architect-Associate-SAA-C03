# AWS Certified Solutions Architect – Associate (SAA-C03)

A structured, practical study guide for designing secure, resilient, high-performing, and cost-aware solutions on AWS. This repository follows the SAA-C03 exam domains and favors service-selection decisions over memorizing product lists.

## Learning roadmap

| # | Topic | What to learn |
|---|---|---|
| 01 | [Cloud fundamentals](01-cloud-fundamentals/README.md) | AWS infrastructure, cloud economics, and the Well-Architected Framework |
| 02 | [IAM and security](02-iam-and-security/README.md) | Identity, permissions, encryption, and layered security |
| 03 | [Compute services](03-compute-services/README.md) | EC2, scaling, containers, and compute selection |
| 04 | [Storage services](04-storage-services/README.md) | Object, block, file, and hybrid storage |
| 05 | [Database services](05-database-services/README.md) | Relational, NoSQL, caching, and analytics data stores |
| 06 | [Networking and content delivery](06-networking-and-content-delivery/README.md) | VPC, routing, load balancing, DNS, and edge delivery |
| 07 | [Application integration](07-application-integration/README.md) | Queues, notifications, events, and workflow orchestration |
| 08 | [Monitoring and management](08-monitoring-and-management/README.md) | Metrics, logs, audit trails, governance, and operations |
| 09 | [Serverless architecture](09-serverless-architecture/README.md) | Event-driven solutions with managed services |
| 10 | [High availability and disaster recovery](10-high-availability-and-disaster-recovery/README.md) | Resilience patterns, backups, and recovery objectives |
| 11 | [Cost optimization](11-cost-optimization/README.md) | Pricing models, rightsizing, and cost governance |
| 12 | [Hands-on labs](12-hands-on-labs/README.md) | Guided, non-deploying exercises and safe console walkthroughs |
| 13 | [Architecture diagrams](13-architecture-diagrams/README.md) | Mermaid reference designs and decision flows |
| 14 | [Practice questions](14-practice-questions/README.md) | Original scenario questions with answer reasoning |
| 15 | [Exam revision](15-exam-revision/README.md) | Comparison tables, checklists, and a final review plan |

### Suggested study sequence

Start with cloud fundamentals, then study security alongside each service domain. Cover compute, storage, databases, networking, integration, and monitoring before moving to serverless and architecture trade-offs. Use the labs to reinforce decisions, then practice explaining why the distractor services do not fit. Finish with the revision sheets and timed question sets.

## Exam domains

The SAA-C03 blueprint groups questions into four domains: Design Secure Architectures, Design Resilient Architectures, Design High-Performing Architectures, and Design Cost-Optimized Architectures. See [exam-domain mapping](15-exam-revision/exam-domain-map.md) for a study crosswalk. Verify current exam details with the [official AWS certification page](https://aws.amazon.com/certification/certified-solutions-architect-associate/).

## Progress tracker

Mark a section complete only after you can explain its key choices without relying on notes.

| Topic | Read | Practice questions | Confidence (1–5) |
|---|:---:|:---:|:---:|
| Cloud fundamentals | [ ] | [ ] | — |
| IAM and security | [ ] | [ ] | — |
| Compute services | [ ] | [ ] | — |
| Storage services | [ ] | [ ] | — |
| Database services | [ ] | [ ] | — |
| Networking and content delivery | [ ] | [ ] | — |
| Application integration | [ ] | [ ] | — |
| Monitoring and management | [ ] | [ ] | — |
| Serverless architecture | [ ] | [ ] | — |
| High availability and disaster recovery | [ ] | [ ] | — |
| Cost optimization | [ ] | [ ] | — |
| Hands-on labs | [ ] | [ ] | — |
| Exam revision | [ ] | [ ] | — |

## Using this repository

- Each topic README introduces the domain and links to focused service or concept notes.
- Mermaid diagrams are source-controlled text; preview them in a GitHub Markdown renderer.
- CLI snippets are for inspection unless explicitly described otherwise. No lab deploys infrastructure by default.
- AWS pricing, service features, and exam content can change. Confirm time-sensitive details in current AWS documentation before acting.
- Never paste account identifiers, credentials, personal data, or sensitive workload information into shared notes.

## Contributions

Keep explanations decision-oriented, link related topics instead of duplicating them, and include the trade-off behind each recommendation. Use original practice questions rather than reproducing copyrighted exam material.
