# Engineering Plugin

A software engineering plugin primarily designed for [Cowork](https://claude.com/product/cowork), Anthropic's agentic desktop application — though it also works in Claude Code. Helps with standups, code review, architecture decisions, incident response, debugging, and technical documentation. Works with any engineering team — standalone with your input, supercharged when you connect your source control, project tracker, and monitoring tools.

## Installation

```bash
claude plugins add knowledge-work-plugins/engineering
```

## Commands

Explicit workflows you invoke with a slash command:

| Command | Description |
|---|---|
| `/standup` | Generate a standup update from your recent activity — commits, PRs, tickets, and chat |
| `/review` | Review code changes — security, performance, style, and correctness |
| `/debug` | Structured debugging session — reproduce, isolate, diagnose, and fix |
| `/architecture` | Create or evaluate architecture decisions — ADR format with trade-off analysis |
| `/incident` | Run an incident response workflow — triage, communicate, mitigate, and write postmortem |
| `/deploy-checklist` | Pre-deployment checklist — verify tests, review changes, check dependencies, confirm rollback plan |

All commands work standalone (paste code, describe your system, upload files).

## Skills

Domain knowledge Claude uses automatically when relevant:

| Skill | Description |
|---|---|
| `code-review` | Review code for bugs, security issues, performance, and maintainability |
| `incident-response` | Triage and manage production incidents — status updates, runbooks, postmortems |
| `system-design` | Design systems and services — architecture diagrams, API design, data modeling |
| `tech-debt` | Identify, categorize, and prioritize technical debt — build a remediation plan |
| `testing-strategy` | Design test strategies — unit, integration, e2e coverage, test plan creation |
| `documentation` | Write and maintain technical documentation — READMEs, API docs, runbooks, onboarding guides |

## Example Workflows

### Morning Standup

```
/standup
```

If your tools are connected, I'll pull your recent commits, PR activity, and ticket updates. Otherwise, tell me what you worked on and I'll format it.

### Code Review

```
/review https://github.com/org/repo/pull/123
```

Share a PR link, paste a diff, or point to files. Get a structured review covering security, performance, correctness, and style.

### Debugging an Issue

```
/debug Users are getting 500 errors on the checkout page
```

Walk through a structured debugging process: reproduce, isolate, diagnose, fix. I'll help you think through it systematically.

### Architecture Decision

```
/architecture Should we use a message queue or direct API calls between services?
```

Get a structured ADR with options analysis, trade-offs, and a recommendation.

### Incident Response

```
/incident The payments service is returning 503s
```

Start an incident workflow: triage severity, draft communications, track timeline, and generate a postmortem when resolved.

### Pre-Deploy Check

```
/deploy-checklist auth-service v2.3.0
```

Get a customized deployment checklist based on your service and what's changing.

## Settings

Create a local settings file at `engineering/.claude/settings.local.json` to personalize:

```json
{
  "name": "Your Name",
  "title": "Software Engineer",
  "team": "Your Team",
  "company": "Your Company",
  "techStack": ["Python", "TypeScript", "PostgreSQL", "AWS"],
  "defaultBranch": "main",
  "deployProcess": "canary"
}
```

The plugin will ask you for this information interactively if it's not configured.
