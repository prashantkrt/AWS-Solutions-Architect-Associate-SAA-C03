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
