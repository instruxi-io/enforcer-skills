# /enforcer-admin

Tenant setup, provider connections, and user/group/role management.

## When to use
- Setting up a new tenant or configuring an existing one
- Connecting OAuth, storage, SMS, or email providers
- Managing users, groups, and roles at scale
- Administering terms of service
- Configuring group challenges

## What it covers
- Tenant creation and configuration
- Connection management (OAuth, storage, SMS, email providers)
- User CRUD and bulk operations
- Group and role management
- Terms of service administration
- Group challenge setup and management

## Tips
- Tenant setup must happen before any other operations for that tenant
- Connections are per-tenant; each tenant configures its own providers
- Role assignments are additive; remove roles explicitly when downgrading access
- Always update both secure and non-secure config files when changing deployment settings
