# Amazon EC2 and scaling

EC2 provides resizable virtual machines. Select an instance family and size for CPU, memory, storage, accelerator, and network needs; validate with measurements rather than choosing by name alone.

## Supporting components

- **AMI:** Image used to launch instances.
- **EBS:** Persistent block volumes; instance store is ephemeral and tied to host lifecycle.
- **Security group:** Stateful traffic filter attached to network interfaces/instances.
- **IAM instance profile:** Supplies temporary role credentials to applications on the instance.
- **Auto Scaling group:** Maintains desired capacity and can scale using policies and health checks.
- **Elastic Load Balancing:** Distributes requests and can stop routing to unhealthy targets.

## Scaling design

Use multiple AZs for availability. Scale out based on a signal related to workload demand (for example, requests per target or queue depth), and account for startup delay. Stateless instances are easier to replace; place session/state data in a suitable shared service. A launch template standardizes instance configuration.

### Common trap

An Auto Scaling group in one AZ can replace failed instances but cannot survive that AZ becoming unavailable. Multi-AZ configuration, health checks, and load balancing must align.
