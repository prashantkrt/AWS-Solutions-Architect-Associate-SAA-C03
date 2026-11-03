# Practice · Storage, databases, and networking

### 1. Shared Linux files

Multiple Linux instances in separate AZs need concurrent access to the same file hierarchy. Which storage type is the best fit?

A. EBS volume attached to each instance · B. EFS file system · C. S3 Glacier Deep Archive · D. Instance store

**Answer: B.** EFS provides managed shared file storage. EBS is block storage and is not a general shared file system; archive object storage and instance store do not match.

### 2. Relational availability

A managed relational database needs standby failover within a Region. Which RDS configuration is designed primarily for that goal?

A. Multi-AZ deployment · B. Read replica only · C. S3 versioning · D. DynamoDB DAX

**Answer: A.** Multi-AZ supports availability/failover. Read replicas are mainly for read scaling and may lag.

### 3. Private outbound connectivity

Instances in a private IPv4 subnet need outbound internet access for updates but should not accept unsolicited internet connections. Which pattern fits?

A. NAT gateway and private-subnet route · B. Internet gateway directly on each instance · C. Public IP on every instance · D. Route 53 private hosted zone only

**Answer: A.** A NAT gateway supports initiated outbound IPv4 connectivity. Route and AZ design must be planned; it is not inbound exposure.

### 4. Burst object archive

Objects are rarely accessed and can tolerate hours for retrieval. Which choice should be evaluated?

A. S3 Glacier Flexible Retrieval or Deep Archive, based on retrieval needs · B. EBS io volume · C. DynamoDB table · D. ALB

**Answer: A.** An archival S3 class may reduce storage cost, but retrieval time, fees, and minimum durations must fit.

### 5. Single-digit-millisecond latency for a gaming studio in one city

A gaming studio needs single-digit-millisecond latency for players concentrated in one city, without standing up a new AWS Region. Which placement option fits?

A. AWS Wavelength · B. Standard Region deployment · C. S3 Transfer Acceleration · D. A second Availability Zone in the nearest Region

**Answer: A.** AWS Wavelength embeds compute and storage inside telecom providers' 5G networks at the edge, so application traffic reaches end users without leaving the telco network — delivering single-digit-millisecond latency to mobile/5G users in a specific metro without deploying a full Region. A standard Region or extra AZ still routes traffic over the public internet/backbone and won't match that latency; Transfer Acceleration only speeds up S3 uploads.

### 6. Why a Wavelength Zone exists vs. an edge location

Why does a Wavelength Zone exist, and how does it differ from a CloudFront edge location?

**Answer:** A Wavelength Zone exists to run latency-sensitive **compute and storage** (EC2, EBS) physically inside a telecom carrier's 5G network, so traffic from mobile devices never has to hop out to the public internet/AWS Region — this matters for use cases like real-time gaming, AR/VR, and connected vehicles. A CloudFront **edge location** instead caches and serves static/dynamic **content** (HTTP responses) close to users as part of the CDN — it does not run general-purpose customer compute like EC2. In short: Wavelength = carrier-network compute for ultra-low-latency apps; edge location = content caching/delivery point for CloudFront.

### 7. Can AWS WAF attach to a Network Load Balancer?

Can AWS WAF be attached to a Network Load Balancer (NLB)?

**Answer: No.** AWS WAF only attaches to resources that operate at Layer 7 (HTTP/HTTPS): Application Load Balancer, Amazon CloudFront, API Gateway, and AppSync. An NLB operates at Layer 4 (TCP/UDP) and has no visibility into HTTP requests, so WAF cannot inspect or filter traffic through it. If WAF protection is needed for traffic that currently passes through an NLB, put an ALB (or CloudFront) in front of the application instead.
