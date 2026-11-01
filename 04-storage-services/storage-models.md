# Block, file, and object storage

| Model | Interface | AWS examples | Think of it as |
|---|---|---|---|
| Block | Volumes attached to a host | EBS, instance store | Disk sectors for an operating system or database |
| File | Shared directory tree and file protocols | EFS, FSx | A network file system shared by clients |
| Object | Objects addressed through an API | S3 | Durable named objects with metadata |

EBS is appropriate for a workload needing a disk volume, while EFS is a shared file system for supported clients and S3 is API-based object storage. Do not select S3 as a drop-in POSIX volume or EFS as a database block device.

For hybrid storage, Storage Gateway can expose selected AWS storage models to on-premises environments. Choose gateway type based on file, volume, or tape compatibility and local caching needs.
