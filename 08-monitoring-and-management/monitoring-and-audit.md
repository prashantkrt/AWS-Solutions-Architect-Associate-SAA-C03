# Monitoring and audit signals

| Question | Signal/service |
|---|---|
| Is CPU, latency, or queue backlog above a threshold? | CloudWatch metrics and alarms |
| What did an application log at a specific time? | CloudWatch Logs (or another configured log destination) |
| Who called an AWS API and from where? | CloudTrail event history/trails |
| Did a resource configuration drift from policy? | AWS Config |
| Can fleet maintenance be automated? | Systems Manager capabilities |

## Architecture practices

- Define service-level indicators and actionable alarms, not just dashboards.
- Ensure logs are retained long enough for investigation while controlling ingestion/storage charges.
- Restrict log access and protect audit records from unauthorized change.
- Centralize account-level visibility where the organization requires it.
- Test alert delivery and runbooks; an alarm with no owner or action is noise.

CloudWatch alarms can react to metrics and configured log filters; CloudTrail records API activity. They are complementary, not interchangeable.
