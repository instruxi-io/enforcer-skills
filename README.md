```
 ███████╗███╗   ██╗███████╗ ██████╗ ██████╗  ██████╗███████╗██████╗ 
 ██╔════╝████╗  ██║██╔════╝██╔═══██╗██╔══██╗██╔════╝██╔════╝██╔══██╗
 █████╗  ██╔██╗ ██║█████╗  ██║   ██║██████╔╝██║     █████╗  ██████╔╝
 ██╔══╝  ██║╚██╗██║██╔══╝  ██║   ██║██╔══██╗██║     ██╔══╝  ██╔══██╗
 ███████╗██║ ╚████║██║     ╚██████╔╝██║  ██║╚██████╗███████╗██║  ██║
 ╚══════╝╚═╝  ╚═══╝╚═╝      ╚═════╝ ╚═╝  ╚═╝ ╚═════╝╚══════╝╚═╝  ╚═╝
                         S K I L L S
```

Claude Code skills for building on the **Enforcer API** — a multi-tenant identity, authorization, and integration platform.

Skills teach your AI agent the *concepts, workflows, and patterns* behind each Enforcer domain. Pair them with the [`enforcer-docs-mcp`](https://github.com/instruxi-io/enforcer-docs-mcp) server for live endpoint discovery and schema resolution.

## Skills

| Skill | Domain | For |
|-------|--------|-----|
| [`/enforcer`](enforcer/) | Getting started — multi-tenancy, roles, auth overview, SDK + MCP setup | Everyone |
| [`/enforcer-auth`](enforcer-auth/) | Authentication flows (SIWE, passkeys, OAuth, OTP, Privy), OPA authorization, verification, terms | Developers |
| [`/enforcer-kv`](enforcer-kv/) | Key-value store — HTTP + gRPC, batch ops, TTL, health checks | Developers |
| [`/enforcer-files`](enforcer-files/) | Object storage (S3/GCS/Storj) + resource sharing intents | Developers |
| [`/enforcer-admin`](enforcer-admin/) | Tenant setup, connections, user/group/role management, terms admin | Tenant Admins |
| [`/enforcer-wallet`](enforcer-wallet/) | Custodial wallets, signing (EIP-191/712/7702/4337), backup via Shamir | Developers |
| [`/enforcer-me`](enforcer-me/) | User profile, contacts, invites, self-service groups | Developers |
| [`/enforcer-message-bus`](enforcer-message-bus/) | Kafka messaging, audit logs, retry | Developers |

## Install

```bash
# Install all skills
for skill in enforcer enforcer-auth enforcer-kv enforcer-files enforcer-admin enforcer-wallet enforcer-me enforcer-message-bus; do
  curl -sL -o ~/.claude/commands/$skill.md \
    https://raw.githubusercontent.com/instruxi-io/enforcer-skills/main/$skill/SKILL.md
done
```

Or install a single skill:

```bash
curl -sL -o ~/.claude/commands/enforcer.md \
  https://raw.githubusercontent.com/instruxi-io/enforcer-skills/main/enforcer/SKILL.md
```

Then use `/enforcer`, `/enforcer-auth`, `/enforcer-kv`, etc. in Claude Code.

## MCP Docs Server

Skills explain the *why and how*. The MCP server provides the *what* — live endpoints, schemas, and auth schemes. Install both for the best experience:

```json
{
  "mcpServers": {
    "enforcer-docs": {
      "command": "npx",
      "args": ["-y", "https://github.com/instruxi-io/enforcer-docs-mcp/releases/latest/download/enforcer-docs-mcp.tgz"]
    }
  }
}
```

## Supported Platforms

Claude Code, Claude Desktop, Cursor, Codex, GitHub Copilot, Windsurf — any tool that supports Claude Code slash commands or can load markdown skill files.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md). Skills should teach patterns and intent, not duplicate endpoint URLs or request schemas (that's the MCP server's job).

## License

MIT
