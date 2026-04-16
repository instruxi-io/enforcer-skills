---
name: enforcer
description: "Getting started with the Enforcer API. Multi-tenancy model, roles (Tenant Admin / Developer / User), auth overview, SDK + MCP setup. Trigger: 'enforcer', 'getting started', 'what is enforcer'"
---

```
 ███████╗███╗   ██╗███████╗ ██████╗ ██████╗  ██████╗███████╗██████╗ 
 ██╔════╝████╗  ██║██╔════╝██╔═══██╗██╔══██╗██╔════╝██╔════╝██╔══██╗
 █████╗  ██╔██╗ ██║█████╗  ██║   ██║██████╔╝██║     █████╗  ██████╔╝
 ██╔══╝  ██║╚██╗██║██╔══╝  ██║   ██║██╔══██╗██║     ██╔══╝  ██╔══██╗
 ███████╗██║ ╚████║██║     ╚██████╔╝██║  ██║╚██████╗███████╗██║  ██║
 ╚══════╝╚═╝  ╚═══╝╚═╝      ╚═════╝ ╚═╝  ╚═╝ ╚═════╝╚══════╝╚═╝  ╚═╝
```

# Enforcer — Getting Started

Enforcer is a multi-tenant identity, authorization, and integration platform run as a managed service. It handles authentication, key-value storage, file storage, wallet infrastructure, messaging, and policy authorization.

## Multi-Tenancy Model

Two-level isolation: **Instance** (dev/staging/prod deployment) and **Tenant** (customer organization within an instance).

Every API call is scoped to a tenant via the caller's JWT. Isolation is enforced at every layer — database rows, Redis key prefixes, storage paths, and Kafka topics all incorporate a tenant hash (8-char hex SHA-256 prefix of the tenant UUID, never the raw UUID).

## Roles

**Tenant Admin** — manages a tenant's configuration: users, groups, roles, connections (OAuth/storage/SMS/email providers), terms of service, and verification challenges. Uses the admin endpoints.

**Developer** — builds applications on top of Enforcer. Integrates auth flows, storage, KV, wallets, and messaging. Uses the SDK and MCP docs server for API discovery.

**User** — an end-user of a tenant's application. Authenticates, manages their profile, stores data, interacts with contacts and groups, uses wallets.

## Environments

| Env | Host |
|-----|------|
| Dev | `enforcer-v2-dev.instruxi.dev` |
| Staging | `enforcer-v2-staging.instruxi.dev` |
| Prod | `enforcer-v2-prod.instruxi.dev` |

Swagger UI is at `/swagger/index.html` on each.

## Authentication

Two mechanisms, both passed as headers:

- **Bearer JWT** (`Authorization: Bearer <token>`) — obtained via login flows (email OTP, SIWE, Google OAuth, Privy, passkeys). Short-lived (15m default), refreshable.
- **API Key** (`X-API-Key: <key>`) — created via the API keys endpoints. Long-lived, suitable for server-to-server.

## SDK

Install `@instruxi-io/enforcer-ts-sdk` from GitHub Packages (requires `read:packages` PAT). Import `Configuration` + the relevant API class, set `basePath` and `apiKey` (the Bearer token).

A Dart/Flutter SDK is also available at `instruxi-io/enforcer-dart-sdk`.

## Using the MCP Docs Server

The `enforcer-docs` MCP server is the primary way to discover endpoints and schemas. Use these tools in order:

1. `list_tags` — find the relevant domain (Auth, KV, Storage, Wallet, etc.)
2. `list_endpoints(tag: "...")` — get endpoint summaries for that domain
3. `get_endpoint(operationId: "...")` — get full request/response shapes with refs resolved
4. `get_schema(name: "...")` — resolve any referenced types
5. `list_auth_schemes` — understand auth requirements

Never hardcode endpoint paths or request bodies from memory — always pull them from the MCP server. The spec is the source of truth.

## Domain Skills

Each domain has its own skill with deeper context:

- `/enforcer-auth` — authentication flows, authorization (OPA), verification, terms
- `/enforcer-kv` — key-value store (HTTP + gRPC)
- `/enforcer-files` — object storage and resource sharing
- `/enforcer-admin` — tenant setup, connections, user/group/role management
- `/enforcer-wallet` — wallet lifecycle, signing, backup/restore
- `/enforcer-me` — user profile, contacts, invites, groups
- `/enforcer-message-bus` — Kafka messaging, audit, retry
