# /enforcer

The getting-started skill. Load this first — it explains what Enforcer is, how multi-tenancy works, what the three roles (Tenant Admin, Developer, User) can do, and how to set up the SDK + MCP docs server.

## When to use

- First time working with the Enforcer API
- Need a refresher on the tenant isolation model
- Setting up the SDK or MCP server
- Deciding which domain skill to load next

## What it covers

- Multi-tenancy model (instance + tenant, tenant hash)
- Role definitions (Tenant Admin, Developer, User)
- Environment URLs (dev/staging/prod)
- Authentication overview (JWT vs API Key)
- SDK setup (TypeScript + Dart)
- MCP docs server tool usage pattern
- Index of all domain skills

## Tips

- Load this skill, then load the domain skill for whatever you're building (e.g., `/enforcer-kv` for key-value work)
- Use the MCP server's `list_tags` tool to see all available API domains before picking a skill
- The skill explains *concepts*; the MCP server provides *live API details*
