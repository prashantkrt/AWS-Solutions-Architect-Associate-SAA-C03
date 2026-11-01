# Lab · Plan a VPC on paper

**Goal:** Practice subnet and route reasoning without provisioning a VPC.

1. Choose a fictional CIDR such as `10.20.0.0/16`; check it does not overlap the organization's real networks.
2. Sketch two AZs, each with a public and private subnet.
3. Add an internet gateway route for public subnets and a NAT egress design for private IPv4 workloads.
4. Mark an ALB in public subnets and application instances in private subnets.
5. Trace a client request and the application's response route.
6. Add a private S3 access path using an appropriate VPC endpoint.
7. Mark which security group and network ACL rules are stateful/stateless.
8. Explain NAT gateway availability/cost trade-offs and what changes if one AZ fails.

**No resources are created.** Do not reuse a production CIDR plan without network-owner review.
