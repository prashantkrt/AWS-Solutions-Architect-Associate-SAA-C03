# 06 · Networking and content delivery

Understand how traffic enters, crosses, and leaves a VPC, and select network services according to reachability and latency needs.

## VPC building blocks

A VPC is a regional network with IPv4/IPv6 CIDR address ranges. CIDR notation defines the network prefix and available address space; plan ranges to avoid overlap with networks that may be connected later. Subnets are AZ-specific. Route tables direct traffic; security groups are stateful, instance/ENI-level controls; network ACLs are stateless subnet-level controls. A public subnet has a route to an internet gateway—assigning a public IP alone does not create a route.

For a step-by-step foundation in IPv4/IPv6, CIDR, subnetting, and public/private addressing, see [IP addressing and subnetting](ip-addressing-and-subnetting.md).

| Requirement | Common choice |
|---|---|
| Outbound internet for private IPv4 workloads | NAT gateway with private-subnet routes |
| Private connectivity to supported AWS services | VPC endpoint (gateway or interface, by service) |
| Private network connection to another VPC | VPC peering for straightforward point-to-point links; Transit Gateway for hub-and-spoke |
| Private dedicated/on-demand connectivity from premises | Direct Connect or Site-to-Site VPN, depending on requirements |
| Global static/dynamic content delivery | CloudFront |
| DNS routing and health checks | Route 53 |

Review [VPC routing and security](vpc-routing.md) and [load balancer selection](load-balancers.md). For connected networks, distinguish point-to-point VPC peering from Transit Gateway hub-and-spoke routing; for private service access, compare gateway and interface VPC endpoints.
