# Load balancer selection

| Type | Layer / routing | Typical fit |
|---|---|---|
| Application Load Balancer (ALB) | HTTP/HTTPS, Layer 7; host/path routing | Web applications and container targets |
| Network Load Balancer (NLB) | TCP/UDP/TLS, Layer 4; high-performance network traffic | Protocol-level traffic or static IP needs |
| Gateway Load Balancer (GWLB) | Layer 3 appliance insertion | Scale third-party virtual network appliances |
| Classic Load Balancer | Legacy option | Existing environments; prefer a modern type for new designs when suitable |

Selection depends on protocol, routing behavior, target types, source address requirements, and performance. Load balancing does not make an application stateless or make a single-AZ target fleet resilient; combine it with healthy targets across AZs.

CloudFront is an edge content delivery service, not a replacement for an application load balancer for every origin. Route 53 provides DNS routing and health-check features, not application request proxying.
