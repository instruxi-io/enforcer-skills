# Contributing

## Adding a New Skill

1. Create a directory: `my-skill/`
2. Add `SKILL.md` with YAML frontmatter (`name`, `description`)
3. Add `README.md` explaining when/why to use the skill
4. Add `VERSION` file containing `1`
5. Open a PR

## Editing an Existing Skill

- Skills teach concepts and workflows, not endpoint details
- Don't hardcode URLs, request bodies, or version numbers
- Point agents to the `enforcer-docs` MCP server for live API details
- Keep skills under ~200 lines
- Don't modify `VERSION` files — CI handles versioning

## PR Guidelines

- Describe what changed and why
- Verify the skill loads correctly as a Claude Code command (`~/.claude/commands/`)
- Test with the `enforcer-docs` MCP server to confirm the MCP references work
