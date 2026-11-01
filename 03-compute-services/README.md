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

An instance combines an instance type, AMI, networking, IAM role, storage, and security groups. Use an Auto Scaling group to replace unhealthy instances and adjust capacity; pair it with a load balancer for traffic distribution. A placement group changes placement behavior, not application-level fault tolerance.

Review [EC2 and scaling](ec2-and-scaling.md) and [compute selection scenarios](compute-selection.md).

## Exam cue

When a question emphasizes minimal administration, prefer managed or serverless options if the application fits their limits. When it requires OS-level access or a specific commercial package, EC2 may be necessary.
