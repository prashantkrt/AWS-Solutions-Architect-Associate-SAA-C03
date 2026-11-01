# 04 · Storage services

Choose storage by access pattern, latency, sharing model, durability, and recovery requirements.

| Service | Model | Typical fit |
|---|---|---|
| Amazon S3 | Object | Durable objects, backups, data lakes, static assets |
| Amazon EBS | Block volume for EC2 | Persistent instance-attached disks and boot volumes |
| Amazon EFS | Managed NFS file system | Shared Linux file access across instances |
| Amazon FSx | Managed file systems | Workloads needing Windows, Lustre, NetApp ONTAP, or OpenZFS compatibility |
| AWS Storage Gateway | Hybrid bridge | Integrate on-premises environments with AWS storage |

## S3 decisions

Use lifecycle policies to transition or expire objects; choose a storage class based on access frequency and retrieval expectations. Versioning helps recover overwritten/deleted objects, while replication supports separate-copy requirements. S3 is not a mounted block disk. Protect buckets with scoped policies, Block Public Access, and encryption appropriate to the workload.

See [S3 storage classes and protection](s3-storage-classes.md) and [block, file, and object storage](storage-models.md).

## Cost and recovery

Account for stored bytes, requests, retrieval, transfer, and replication. EBS snapshots are incremental backups, not a substitute for application-consistent recovery planning. Test restores rather than assuming a backup is usable.
