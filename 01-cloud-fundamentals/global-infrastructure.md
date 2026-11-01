# AWS Global Infrastructure

Covers the Module 1 syllabus topics: data centers (DC), Availability Zones (AZ), Local Zones (LZ), Wavelength Zones (WZ), and WAF. Regions, edge locations, and Outposts are added because SAA-C03 expects them alongside these topics.

> **Syllabus check:** The shared outline (DC, AZ, LZ, WZ, WAF) is valid for SAA-C03 but incomplete. Add **Regions**, **edge locations / Regional edge caches**, and **AWS Outposts**. Also, **WAF is a security service, not infrastructure**; it is introduced here for context and studied in depth with Shield and Firewall Manager in the edge/security modules.

## Hierarchy

| Component | What it is | Exam cue |
|---|---|---|
| Data center (DC) | Physical facility with servers, storage, networking, power, and cooling. Not directly selectable. | Operated and secured by AWS (shared responsibility) |
| Availability Zone (AZ) | One or more discrete DCs in a Region with independent power, cooling, and networking, connected by low-latency links. | Deploy across 2+ AZs for high availability |
| Region | A geographic area containing multiple (typically 3+) AZs. Isolated from other Regions. | Choose by latency, compliance/data residency, service availability, and price |
| Local Zone (LZ) | An extension of a Region placing compute, storage, and select services close to a large metro area. Subnets are created in it from the parent Region's VPC. | Single-digit-millisecond latency for end users, e.g. media rendering, gaming, live video |
| Wavelength Zone (WZ) | AWS infrastructure embedded in telecom providers' 5G networks. | Ultra-low latency for mobile/5G apps, e.g. AR/VR, connected vehicles |
| Edge location | Site used by CloudFront, Route 53, and Global Accelerator to cache content and reduce latency. Far more numerous than Regions. | Content delivery, not for running your EC2 workloads |
| Regional edge cache | Larger cache between CloudFront edge locations and the origin. | Keeps less-popular content closer than the origin |
| AWS Outposts | AWS-managed racks/servers installed in your own data center. | Low latency to on-premises systems or local data processing with the AWS API |

## Opt-in and service scope

- Most Regions are enabled by default; some newer Regions must be **opted in**.
- Local Zones and Wavelength Zones must also be **opted in** (enabled per account) before use.
- Services are either **Regional** (e.g. S3 buckets, VPC, DynamoDB), **zonal** (EC2 instances, EBS volumes, subnets), or **global** (IAM, Route 53, CloudFront, WAF for CloudFront).
- AZ names (e.g. `us-east-1a`) are mapped per account; use **AZ IDs** (e.g. `use1-az1`) to align AZs across accounts.

## AWS WAF (introduction)

AWS WAF is a web application firewall operating at layer 7 (HTTP/HTTPS).

- Attach to: CloudFront, Application Load Balancer, API Gateway, AppSync, Cognito user pools.
- Not attachable to Network Load Balancers or directly to EC2.
- Uses web ACLs with rules and rule groups: IP sets, geo-match, rate-based rules, SQL injection and XSS protections, and managed rule groups.
- WAF protects against application-layer exploits; **AWS Shield** protects against DDoS, and **Firewall Manager** manages policies across accounts.
- For CloudFront, create the web ACL in **us-east-1** (global scope).

## Choosing the right placement

| Requirement | Choice |
|---|---|
| Survive a data-center or AZ failure | Multi-AZ |
| Survive a regional failure or serve distant users | Multi-Region |
| Low latency to a specific metro area | Local Zone |
| Low latency for 5G mobile devices | Wavelength Zone |
| Cache static/dynamic content globally | CloudFront edge locations |
| AWS services on premises | Outposts |
| Block SQL injection / XSS / bad bots on web apps | AWS WAF |

## Check your understanding

1. Which placement option fits a gaming studio needing single-digit-millisecond latency in one city without a new Region?
2. Why does a Wavelength Zone exist, and how does it differ from an edge location?
3. Can AWS WAF be attached to a Network Load Balancer?
