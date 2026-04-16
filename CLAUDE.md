# Contribution Guidelines for Claude

When modifying skills in this repo:

## Principles

1. **Skills teach patterns and intent.** They explain *why* something works the way it does and *how* workflows connect. They do NOT list endpoint URLs or request/response schemas — that's the MCP server's job.

2. **Point agents to the MCP server.** Every skill should end with guidance like "Use `list_endpoints(tag: '...')` from the `enforcer-docs` MCP server to discover endpoints."

3. **Keep skills durable.** Avoid anything that goes stale when the API changes — no hardcoded paths, no version numbers, no request body examples. Concepts and workflows are stable; URLs are not.

4. **One skill, one domain.** Each skill covers a coherent domain. Don't cross boundaries (e.g., don't explain wallet signing in the auth skill).

## File Structure

Each skill directory contains:

- `SKILL.md` — the skill itself (loaded by Claude Code as a slash command). Has YAML frontmatter with `name` and `description`.
- `README.md` — user-facing guide: when to use the skill, what it covers, tips.
- `VERSION` — auto-incremented integer on each merge to main.

## SKILL.md Format

```markdown
---
name: skill-name
description: "One-line description. Trigger: /skill-name"
---

# Title

Content here. Teach concepts, not endpoints.
```

## When Editing

- Do not remove the YAML frontmatter
- Do not add endpoint URLs or request/response bodies
- Do not modify VERSION files (auto-managed by CI)
- Test that the skill loads correctly as a Claude Code command
- Keep each skill under ~200 lines — concise beats comprehensive
