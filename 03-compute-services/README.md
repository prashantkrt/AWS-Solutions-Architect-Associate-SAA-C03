# 03 · Compute services

Match compute to operating-system control, workload shape, scaling behavior, and operational overhead.

| Option | Best fit | Trade-off |
|---|---|---|
| Amazon EC2 | Full OS control, custom software, specialized instance needs | You manage guest OS, patching, and capacity design |
| AWS Lambda | Short-lived event-driven code with variable demand | Runtime, execution, and integration constraints apply |
| Amazon ECS / EKS | Containerized applications; ECS integrates with AWS, EKS provides Kubernetes | Cluster and platform choices add operational complexity |
| AWS Fargate | Run ECS/EKS tasks without managing worker instances | Less host control; evaluate task sizing and pricing |
| Elastic Beanstalk | Deploy common web applications with managed environment provisioning | Less low-level control than designing resources directly |

## EC2 essentials

An instance combines an instance type, AMI, networking, IAM role, storage, and security groups. Instance families target different workload profiles (such as general purpose, compute, memory, or storage optimization). Compare On-Demand, Spot, and commitment-based pricing against flexibility and usage certainty; include EBS and data-transfer charges when estimating cost.

Use an Auto Scaling group to replace unhealthy instances and adjust capacity; pair it with a load balancer for traffic distribution. A placement group changes placement behavior, not application-level fault tolerance.

## Automation and deployment

- **AWS CloudFormation** provisions and updates AWS resources from templates, providing infrastructure as code and repeatable environments.
- **Elastic Beanstalk** deploys and operates common application stacks while managing much of the underlying environment setup. It is a platform service, not a replacement for understanding the resources it provisions.

Review [EC2 and scaling](ec2-and-scaling.md) and [compute selection scenarios](compute-selection.md).

## Exam cue

When a question emphasizes minimal administration, prefer managed or serverless options if the application fits their limits. When it requires OS-level access or a specific commercial package, EC2 may be necessary.
