# 01 · Cloud fundamentals

Understand the foundational concepts behind AWS architecture before comparing individual services.

## Study guide

- **Global infrastructure:** A Region is a separate geographic area; Availability Zones (AZs) are isolated locations within a Region; edge locations support services such as CloudFront. Multi-AZ designs improve availability, while multi-Region designs address broader regional failure or latency needs.
- **Shared responsibility:** AWS secures the cloud infrastructure. Customers secure what they run in the cloud, including identities, data, configurations, and (depending on service) guest operating systems. The boundary changes with the service.
- **Elasticity and agility:** Provision resources as demand changes, and automate repeatable operations. Elasticity is not the same as high availability.
- **Well-Architected thinking:** Evaluate operational excellence, security, reliability, performance efficiency, cost optimization, and sustainability together; improvements in one area can create trade-offs elsewhere.
- **Cloud economics:** Distinguish capital expense from variable operating expense. Pay-as-you-go does not mean every service is inexpensive; idle and overprovisioned resources still incur costs.

## Choose the right scope

| Requirement | Common design direction |
|---|---|
| Tolerate a single data-center/AZ issue | Distribute resources across multiple AZs |
| Reduce latency for global users | Use edge delivery and locate compute/data appropriately |
| Recover after a regional event | Define RTO/RPO, then select a multi-Region recovery strategy |
| Avoid maintaining physical capacity | Prefer managed services where their constraints fit |

## Further reading

- [Shared responsibility and security boundaries](shared-responsibility.md)
- [AWS CLI: inspect identity and Regions](aws-cli-basics.md)

## Check your understanding

Can you explain why using multiple AZs is different from using multiple Regions, and identify which parts of an EC2 workload remain your responsibility?
