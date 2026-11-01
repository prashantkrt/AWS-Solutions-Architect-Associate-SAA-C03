# Pricing models and cost controls

## Compute pricing choices

- **On-Demand:** No long-term commitment; suitable for experimentation or variable usage.
- **Savings Plans:** Commitment-based discounts for eligible compute usage; flexibility depends on plan type and terms.
- **Reserved Instances:** Commitment discounts for eligible services/configurations; understand scope and exchange/modify rules.
- **Spot:** Uses spare capacity at a discount, with possible interruption; design retryable/checkpointed work.

Do not buy commitments solely to meet a target discount. First establish a stable baseline, then evaluate coverage, utilization, and risk.

## Cost visibility and optimization

Use Cost Explorer for trends, budgets/alerts for thresholds, tags for allocation, and anomaly detection for unusual changes. Review network egress, NAT processing, storage requests/retrieval, idle load balancers, snapshots, database I/O, and log retention.

Before optimization, confirm performance, availability, and retention requirements. Deleting backups or choosing a single-AZ design to lower spend can violate recovery objectives.
