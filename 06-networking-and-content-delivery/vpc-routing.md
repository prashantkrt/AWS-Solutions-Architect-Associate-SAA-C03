# VPC routing and security

## Packet path checklist

For a connection, check each hop: source address and route, subnet route table, gateway/endpoint, destination route, security group, network ACL, and application listener. A single missing return path can break communication.

- A route to an internet gateway plus appropriate addressing can make a subnet public. A private subnet commonly uses a NAT gateway for outbound IPv4 internet connectivity.
- NAT gateways allow initiated outbound connections; they do not make private instances directly reachable from the internet.
- Security groups are stateful and allow rules only. Network ACLs are stateless and evaluate inbound/outbound rules separately.
- A VPC endpoint can keep traffic to supported AWS services off the public internet. Gateway endpoints support S3 and DynamoDB; interface endpoints use PrivateLink for supported services.
- VPC peering is non-transitive. Transit Gateway supports hub-and-spoke connectivity and routing across attached networks.

## Safe design checks

Avoid overlapping CIDRs across networks you expect to connect. Use separate subnets across AZs for resilient workloads. Restrict administrative access and prefer managed session mechanisms over open inbound SSH/RDP.
