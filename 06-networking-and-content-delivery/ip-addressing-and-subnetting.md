# IP addressing and subnetting

This guide covers the address and subnet fundamentals used to plan an AWS VPC. Start with the address range, divide it into subnets, then decide how each subnet should route traffic.

## IP address basics

An IP address identifies a network interface so that traffic can be routed to it.

- **IPv4** uses 32-bit addresses, usually written as four decimal octets, such as `192.168.1.10`. Each octet ranges from 0 to 255.
- **IPv6** uses 128-bit addresses written in hexadecimal and separated by colons, such as `2001:db8:1::10`. IPv6 provides a much larger address space and does not use NAT for address conservation in the same way IPv4 commonly does.
- **Private IPv4 addresses** are reserved for use inside private networks and are not routed on the public internet. The private ranges are `10.0.0.0/8`, `172.16.0.0/12`, and `192.168.0.0/16`.
- **Public IPv4 addresses** are globally routable addresses. In AWS, an instance generally needs both a public IPv4 address and a route through an internet gateway to communicate directly with the internet; security group and network ACL rules still control traffic.
- **Elastic IP addresses** are static public IPv4 addresses allocated to an AWS account. They can be associated with supported resources and reassociated when needed. An automatically assigned public IPv4 address is not a permanent address.

An IPv6 address assigned from a VPC's IPv6 range is globally unique and can be internet-routable when routes and security rules allow it. Do not treat a public address as permission to connect: routing and network controls still apply.

## CIDR notation

Classless Inter-Domain Routing (CIDR) notation represents an address range as a network address followed by a prefix length. For example, `10.0.0.0/16` identifies a range whose first 16 bits are the network prefix. The remaining bits identify addresses within that range.

For IPv4, the number of addresses in a CIDR block is `2^(32 - prefix length)`. A smaller prefix number therefore represents a larger range.

| IPv4 CIDR | Total addresses | Example use |
|---|---:|---|
| `10.0.0.0/16` | 65,536 | A VPC address range |
| `10.0.1.0/24` | 256 | A subnet within that VPC |
| `10.0.1.0/26` | 64 | A smaller subnet |

These are total IPv4 addresses, not necessarily the number an AWS subnet can assign to resources. AWS reserves five IPv4 addresses in every subnet: the first four and the final address. For example, a `/24` has 256 total addresses and 251 usable addresses in AWS.

IPv6 prefix lengths work the same way, but the address size is 128 bits. AWS VPC IPv6 CIDR ranges are much larger than typical IPv4 ranges; plan IPv6 separately rather than assuming an IPv4 subnet size translates directly.

## Subnetting

Subnetting divides a larger network range into smaller, non-overlapping ranges. Each AWS subnet belongs to one Availability Zone, while a VPC can span multiple Availability Zones.

Example: divide `10.0.0.0/24` into four equal subnets by borrowing two host bits. The prefix grows from `/24` to `/26`, giving four blocks of 64 total IPv4 addresses:

| Subnet CIDR | Address range | AWS-usable IPv4 addresses |
|---|---|---:|
| `10.0.0.0/26` | `10.0.0.0`–`10.0.0.63` | 59 |
| `10.0.0.64/26` | `10.0.0.64`–`10.0.0.127` | 59 |
| `10.0.0.128/26` | `10.0.0.128`–`10.0.0.191` | 59 |
| `10.0.0.192/26` | `10.0.0.192`–`10.0.0.255` | 59 |

Choose non-overlapping VPC and subnet ranges, leaving room for growth and future connections to other VPCs or on-premises networks. Overlapping ranges complicate or prevent routing between connected networks. AWS IPv4 subnet CIDR blocks must be between `/16` and `/28`.

## Public and private subnets

“Public” and “private” describe routing, not the numerical range of the subnet's IP addresses:

- A **public subnet** has a route to an internet gateway. A resource also needs suitable addressing and security rules for direct internet communication.
- A **private subnet** does not have a direct route to an internet gateway. For outbound IPv4 internet access, it commonly routes through a NAT gateway in a public subnet.
- A **public IP address alone** does not make a subnet public or create a route to the internet.

Route tables control where traffic goes. Security groups are stateful controls applied to network interfaces; network ACLs are stateless controls applied at the subnet boundary. Review [VPC routing and security](vpc-routing.md) for packet paths and gateway choices.

## AWS address planning checklist

- Select VPC CIDR ranges that do not overlap with networks you may connect.
- Allocate separate subnets in multiple Availability Zones for resilient workloads.
- Size IPv4 subnets for AWS's five reserved addresses as well as workload growth.
- Decide whether each subnet needs inbound or outbound internet connectivity, then configure routes and security controls accordingly.
- Plan IPv4 and IPv6 ranges and routes independently.
