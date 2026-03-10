# loomcrafthq/agents

Universal AI agents for Claude Code, Cursor, and other agent runtimes.

## Agents

| Slug | Name | Description |
|------|------|-------------|
| `backend` | Backend | Use for any server-side task: API endpoints, business logic, authentication, authorization, middleware, and backend architecture. |
| `database` | Database | Use for schema design, migrations, query optimization, seed data, and data integrity enforcement. |
| `frontend` | Frontend | Use for UI components, pages, layouts, client-side state, accessibility (WCAG 2.1 AA), and performance optimization. |
| `review-qa` | Review QA | Use for code review and quality analysis. Read-only — reports findings with severity and actionable recommendations. |
| `security` | Security | Use for security audits, vulnerability detection (OWASP Top 10), and secure coding pattern enforcement. |
| `tester` | Tester | Use for writing and running unit, integration, and end-to-end tests following the testing pyramid. |
| `ux-ui` | UX/UI | Use for design systems, component styling, interaction patterns, usability heuristics, and responsive design. |

## Convention

Each agent is defined by an `AGENT.md` file inside its directory. The file uses the following format:

```markdown
---
name: Agent Name
description: "Use for [specific tasks this agent handles]."
model: inherit
tools: ["Read", "Edit", "Write", "Bash", "Grep", "Glob"]
---

Detailed instructions for the agent in Markdown.
```

**Frontmatter fields:**

- `name` -- Display name of the agent.
- `description` -- Short description optimized for routing: starts with "Use for..." so the orchestrator knows when to invoke it.
- `model` -- The model the agent should use. Use `inherit` to use the parent model, or specify a model ID (e.g., `claude-sonnet-4-6`).
- `tools` -- JSON array of tools the agent is allowed to invoke.

The Markdown body contains the full system prompt: role definition, investigation protocol, tool usage guidance, domain rules, examples, anti-patterns, safety guardrails, handoff patterns, and a self-check section.

## Usage

```sh
loomcraft add loomcrafthq/agents/<slug>
```

For example, to add the backend agent:

```sh
loomcraft add loomcrafthq/agents/backend
```

## Community

Anyone can create and share agents using the same convention. To contribute:

1. Create a public repository with one or more agent directories.
2. Each directory must contain an `AGENT.md` file following the frontmatter + Markdown body format described above.
3. Register your agents in an `agents.json` at the root of your repository (same schema as this repo).
4. Others can install your agents with `loomcraft add <owner>/<repo>/<slug>`.

Pull requests to this repository are welcome for agents that are broadly useful, stack-agnostic, and follow the existing quality bar.

## License

MIT
