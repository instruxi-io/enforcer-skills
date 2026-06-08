# /enforcer-tenant

Create a new tenant or update an existing tenant's config over the REST API.

## When to use
- Updating a tenant's branding, app URL, payment link, or join policy
- Setting `app_url` / `payment_link_url` so check-in & invite emails point at the right app
- Creating a new tenant
- Activating / deactivating a tenant
- Pasting freeform tenant details and having them applied for you

## What it covers
- Resolving a tenant by name or code
- The full `tenants` field set and their allowed values (status, auth/wallet provider, self-join policy)
- The `app_url` vs `payment_link_url` distinction
- A confirm-first update flow: parse → diff → confirm → PATCH → verify
- Tenant creation via the API (so Kafka topics get bootstrapped)

## Tips
- Always discover the exact endpoint + request body from the `enforcer-docs` MCP — don't hardcode paths
- Confirm the environment (dev/staging/prod) and show a before→after diff before any prod write
- Updates are tri-state: omit = no change, `""` = clear, value = set
- Link changes only affect newly issued check-in/invite emails; already-sent links are baked at issue time
- Create through the API, never a raw DB insert (the create path bootstraps the tenant's Kafka topics)
