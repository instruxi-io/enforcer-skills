# /enforcer-message-bus

Kafka-based message publishing, audit logging, and event delivery.

## When to use
- Building event-driven workflows between services
- Setting up audit trails for compliance
- Replacing webhook-based integrations with reliable message delivery
- Monitoring message statistics and retry status

## What it covers
- Message publishing to Kafka topics
- Audit log creation and querying
- Retry mechanics for failed deliveries
- Message and topic statistics

## Tips
- Consumer groups are scoped by instance ID to prevent cross-environment interference
- Audit logs are append-only; use query filters for efficient retrieval
- Failed messages are retried automatically; check statistics to monitor dead letters
- Prefer the message bus over direct HTTP callbacks for reliability
