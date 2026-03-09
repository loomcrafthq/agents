# loomcrafthq/agents

Universal AI agents for Claude Code, Cursor, and other agent runtimes.

## Agents

| Slug | Name | Description |
|------|------|-------------|
| `backend` | Backend | Designs APIs, implements business logic, handles authentication patterns, and enforces clean architecture on the server side. |
| `database` | Database | Designs schemas, writes migrations, optimizes queries, and enforces data integrity using universal database principles. |
| `frontend` | Frontend | Builds UI components, manages client-side state, enforces accessibility (WCAG 2.1 AA), and optimizes performance (Core Web Vitals). |
| `review-qa` | Review QA | Reviews code for quality, security, and performance issues. Reports findings with severity and actionable recommendations. |
| `security` | Security | Audits code for vulnerabilities using OWASP Top 10, enforces secure coding patterns, and reports findings with remediation steps. |
| `tester` | Tester | Writes unit, integration, and end-to-end tests following the testing pyramid, TDD/BDD, and Arrange-Act-Assert patterns. |
| `ux-ui` | UX/UI | Applies usability heuristics, designs accessible interfaces, maintains design system tokens, and crafts responsive interaction patterns. |

## Convention

Each agent is defined by an `AGENT.md` file inside its directory. The file uses the following format:

```markdown
---
name: Agent Name
description: One-line description of what the agent does.
model: claude-sonnet-4-20250514
tools: ["tool1", "tool2"]
---

Detailed instructions for the agent in Markdown.
```

**Frontmatter fields:**

- `name` -- Display name of the agent.
- `description` -- Short description of the agent's role.
- `model` -- The model the agent should use.
- `tools` -- List of tools the agent is allowed to invoke.

The Markdown body contains the full system prompt: rules, constraints, output format, and any domain-specific guidance the agent follows.

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
