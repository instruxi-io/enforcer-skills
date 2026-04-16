# /enforcer-kv

Key-value store with TTL support, accessible via HTTP and gRPC.

## When to use
- Storing and retrieving per-user or per-tenant data
- Building feature flags or configuration toggles
- Implementing caching layers
- Rate limiting or counters
- Batch read/write operations

## What it covers
- CRUD operations on key-value pairs with optional TTL
- HTTP and gRPC transport layers
- Batch get/set/delete operations
- Health and readiness endpoints
- Multi-tenant key isolation via tenant hash

## Tips
- Keys are automatically scoped by instance, tenant, and user
- TTL is optional; omit it for persistent storage
- Use batch endpoints when operating on multiple keys to reduce round trips
- The health endpoint checks Redis connectivity
