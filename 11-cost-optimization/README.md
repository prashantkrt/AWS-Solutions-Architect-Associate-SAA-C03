# 11 · Cost optimization

Optimize for the required outcome and lifecycle, not simply the lowest hourly rate.

## Practical levers

- Right-size compute and databases from observed utilization.
- Use Auto Scaling and schedules where workloads are intermittent.
- Select EC2 On-Demand, Spot, or commitment discounts according to flexibility and usage certainty.
- Apply S3 lifecycle transitions, retention, and deletion policies that match recovery needs.
- Use budgets, Cost Explorer, cost allocation tags, and anomaly detection to make spend visible.
- Reduce unnecessary data transfer, idle resources, and excessive log retention.

| Pricing choice | Suitable when | Main risk/trade-off |
|---|---|---|
| On-Demand | Variable demand or short-term use | Unit price can be higher |
| Savings Plans / Reserved Instances | Stable eligible usage and commitment confidence | Commitment reduces flexibility; terms vary |
| Spot Instances | Interruptible, fault-tolerant work | Capacity can be reclaimed |

See [pricing and savings choices](pricing-models.md). Always check current regional pricing and terms; do not infer total cost from compute price alone.
