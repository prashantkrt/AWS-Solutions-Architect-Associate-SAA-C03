# AWS Global Infrastructure

Covers the Module 1 syllabus topics: data centers (DC), Availability Zones (AZ), Local Zones (LZ), Wavelength Zones (WZ), and WAF. Regions, edge locations, and Outposts are added because SAA-C03 expects them alongside these topics.

> **Syllabus check:** The shared outline (DC, AZ, LZ, WZ, WAF) is valid for SAA-C03 but incomplete. Add **Regions**, **edge locations / Regional edge caches**, and **AWS Outposts**. Also, **WAF is a security service, not infrastructure**; it is introduced here for context and studied in depth with Shield and Firewall Manager in the edge/security modules.

## Hierarchy

### Diagram (labels only: DC, AZ, Region, LZ, WZ, Edge)

```
                               REGION
                    +-----------------------------+
                    |                              |
              +-----v-----+                 +------v----+
              |    AZ-1   |<--------------->|    AZ-2    |
              +-----+-----+   low-latency   +-----+------+
                    |            link             |
           +--------+--------+            +-------+-------+
           v                 v             v               v
        +----+            +----+        +----+          +----+
        | DC |<---------->| DC |        | DC |<-------->| DC |
        +----+            +----+        +----+          +----+


                    REGION (parent)
                    +-----------------------------+
                    |                              |
              +-----v-----+                        |
              |    AZ     |                        |
              +-----+-----+                        |
                    |                              |
                    | extends out to               | extends out to
                    v                              v
              +-----------+                    +-----------+
              |    LZ     |                    |    WZ     |
              | (metro    |                    | (inside   |
              |  city)    |                    | telco 5G) |
              +-----------+                    +-----------+


   EDGE LOCATIONS (global network, separate from Regions)

        END USER                 END USER                END USER
           |                         |                        |
           v                         v                        v
      +---------+              +---------+              +---------+
      |  EDGE   |              |  EDGE   |              |  EDGE   |
      | (Cloud- |              | (Cloud- |              | (Cloud- |
      | Front   |              | Front   |              | Front   |
      | cache)  |              | cache)  |              | cache)  |
      +----+----+              +----+----+              +----+----+
           |   cache hit -----> serve user directly from cache
           |   cache miss
           v
      +-----------------+
      | REGIONAL EDGE   |
      |     CACHE       |
      +--------+--------+
               |
               v
      +-----------------+
      |  ORIGIN (Region/ |
      |  S3 / ALB / EC2) |
      +-----------------+
```

```
AWS GLOBAL INFRASTRUCTURE — NOTEPAD VIEW
=========================================

AWS CLOUD (all Regions worldwide)
|
|-- REGION  (e.g. us-east-1, N. Virginia)
|   "A geographic area, isolated from other Regions"
|   |
|   |-- AVAILABILITY ZONE (AZ)              AVAILABILITY ZONE (AZ)
|   |   us-east-1a                          us-east-1b   ...(3+ AZs per Region)
|   |   |                                    |
|   |   |-- DATA CENTER (DC)                 |-- DATA CENTER (DC)
|   |   |-- DATA CENTER (DC)                 |-- DATA CENTER (DC)
|   |   (1+ physical buildings per AZ,       (independent power/cooling/network,
|   |    isolated failure domain)             low-latency link back to other AZs)
|   |
|   |-- LOCAL ZONE (LZ)   <-- extension of THIS Region, placed in a distant metro
|   |     e.g. us-west-2-lax-1a (parent Region: us-west-2, city: Los Angeles)
|   |     - your VPC subnet reaches in here directly
|   |     - runs EC2 / EBS close to that city's users
|   |     - use when: low latency needed in a city with NO nearby Region
|   |
|   |-- WAVELENGTH ZONE (WZ)   <-- extension of THIS Region, embedded INSIDE
|   |     e.g. us-east-1-wl1-bos-wlz-1      a telecom carrier's 5G network
|   |     - your VPC subnet reaches in here via a Carrier Gateway
|   |     - runs EC2 / EBS physically inside the mobile carrier's network
|   |     - use when: 5G / mobile-carrier traffic needs ultra-low latency
|
|-- EDGE LOCATION(S)   <-- NOT part of a Region; a separate global network
|     used by: CloudFront, Route 53, Global Accelerator
|     - caches/serves content close to users worldwide
|     - far more edge locations than Regions
|     - does NOT run your EC2 workloads
|
|-- REGIONAL EDGE CACHE   <-- sits between edge locations and the origin Region
      bigger cache, holds less-popular content longer


QUICK MENTAL MODEL
-------------------
DC            -> the building
AZ            -> a cluster of 1+ buildings, isolated power/network
Region        -> a cluster of 3+ AZs, isolated from other Regions
Local Zone    -> "a mini-AZ" dropped into a faraway city, parented to a Region
Wavelength    -> "a mini-AZ" dropped INSIDE a telecom's 5G network, parented to a Region
Edge location -> not compute at all; just content caching, all over the world
```

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


### LZ vs WZ — simple diagram

```
REGION ---> LZ   (Local Zone: AWS building, in a metro city)

REGION ---> VPC ---> Carrier Gateway ---> TELCO 5G NETWORK ---> WZ (AWS servers, hosted inside telco) ---> 5G device
```

- LZ attaches straight to the **Region** (not to any one AZ).
- WZ's servers are **AWS-owned**, just physically racked **inside the telco's** network site.

### Wavelength Zone — dedicated connection diagram

```
 AWS REGION                         TELCO 5G NETWORK (carrier-owned)
+-----------+                      +----------------------------------+
|           |                      |                                  |
|   VPC     |---Carrier Gateway--->|   WAVELENGTH ZONE                |
|           |   (AWS <-> telco     |   (AWS-owned EC2/EBS servers,    |
+-----------+    link)             |    physically racked inside      |
                                   |    the telco's site)             |
                                   |          |                       |
                                   |          v                       |
                                   |   TELCO 5G RADIO NETWORK          |
                                   +----------+-----------------------+
                                              |
                                              v
                                       +-------------+
                                       |  5G DEVICE  |
                                       | (END USER)  |
                                       +-------------+

Path: VPC (AWS Region) -> Carrier Gateway -> Wavelength Zone (AWS servers, inside telco)
      -> Telco's own 5G radio network -> End user's 5G device
```

- Traffic never has to exit the telco network and go back to the AWS Region — that's what removes the latency.
- Only the **Carrier Gateway hop** crosses from AWS's side into the telco's side; everything after that (radio network, last mile to device) is the telco's infrastructure.

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

### Answers

1. **A Local Zone.** It extends a parent Region's compute/storage/subnets into a specific metro area, giving single-digit-millisecond latency to end users there without deploying a whole new Region. (A Wavelength Zone also gives ultra-low latency, but specifically for traffic on telecom 5G networks, not general metro users.)
2. A **Wavelength Zone** exists to embed AWS compute and storage directly inside telecom providers' 5G networks, so mobile/5G traffic (AR/VR, connected vehicles, gaming) never has to leave the carrier network to reach the application — minimizing latency. An **edge location** is different in purpose and kind: it's a CloudFront/Route 53/Global Accelerator site that caches and delivers content, not a place where you run EC2 workloads.
3. **No.** WAF operates at layer 7 and only attaches to CloudFront, Application Load Balancer, API Gateway, AppSync, and Cognito user pools — not Network Load Balancers (layer 4) or directly to EC2.
