# Knowledge Work Plugins (Connector-Free)

A connector-free fork of Anthropic's [knowledge-work-plugins](https://github.com/anthropics/knowledge-work-plugins).

Upstream ships each plugin with pre-configured MCP servers (`.mcp.json` + `CONNECTORS.md`) to wire Claude into Slack, Notion, Jira, CRMs, data warehouses, and other tools. This fork removes all of that and keeps only the **skills and slash commands**, which contain the domain knowledge and workflows and run standalone with no external connections.

You provide context manually (paste text, upload files, describe the situation) and Claude does the work. No MCP servers, no OAuth, no connector setup.

## What changed from upstream

- Deleted all `*.mcp.json` (21 files) and `CONNECTORS.md` (17 files)
- Removed connector docs, setup tables, and "supercharged with MCP" sections from READMEs
- Stripped connector references from skill prose (placeholders, "If Connectors Available" sections, connected-tool workflows) so every skill is knowledge/instructional and runs from data you provide
- Removed skills and plugins whose value depended on the connectors: `enterprise-search`, `pdf-viewer`, `partner-built/apollo`, `partner-built/slack`, `partner-built/common-room`, and most of `small-business` (see its README)

Everything else is upstream: same skills, same commands, same file layout. Where a skill mentions a tool (Zoom MCP, DocuSign, QuickBooks, etc.), it is either educational reference material or guidance for the *user* to operate that tool themselves — never an automatic connection.

## Plugins included

| Plugin | How it helps |
|--------|-------------|
| **[productivity](./productivity)** | Tasks, daily workflows, and personal context |
| **[sales](./sales)** | Prospect research, call prep, pipeline review, outreach drafts |
| **[customer-support](./customer-support)** | Ticket triage, response drafts, escalations, KB articles |
| **[product-management](./product-management)** | Specs, roadmaps, research synthesis, stakeholder updates |
| **[marketing](./marketing)** | Content, campaigns, brand voice, competitive briefs, performance reports |
| **[legal](./legal)** | Contract review, NDA triage, compliance, risk, briefs |
| **[finance](./finance)** | Journal entries, reconciliations, statements, variances, close, audit |
| **[data](./data)** | SQL, data exploration, visualization, dashboards, validation |
| **[bio-research](./bio-research)** | scRNA-seq QC, scvi-tools, Nextflow, Allotrope, problem selection |
| **[cowork-plugin-management](./cowork-plugin-management)** | Create or customize plugins for your org |
| **[operations](./operations)** | Vendor, process, change, capacity, status, runbooks |
| **[human-resources](./human-resources)** | Offers, onboarding, reviews, policy, comp, reporting |
| **[design](./design)** | Critique, design systems, handoff, UX copy, accessibility, research |
| **[small-business](./small-business)** | Hiring, contracts, pricing, cash flow, and customer handling (data provided by you) |

Partner-built plugins (`partner-built/*`) are also included without their MCP servers. See their READMEs for standalone limitations.

## Getting started

### Cowork

Install from **Settings → Plugins** or copy a plugin folder into your Cowork plugins directory.

### Claude Code

```bash
# add this fork as a marketplace
claude plugin marketplace add <this-repo-url>

# install a plugin
claude plugin install productivity@knowledge-work-plugins-fork
```

Once installed, skills activate automatically and slash commands are available (e.g. `/sales:call-prep`, `/data:write-query`, `/finance:reconciliation`).

## How plugins work

```
plugin-name/
├── .claude-plugin/plugin.json   # manifest
├── commands/                    # slash commands you invoke explicitly
└── skills/                      # domain knowledge Claude uses automatically
```

- **Skills**: markdown workflows Claude loads when relevant (no code needed)
- **Commands**: explicit actions (e.g. `/legal:review-contract`, `/marketing:draft-content`)
- File-based: markdown and JSON, no build step, no infrastructure

Because there are no connectors, every workflow that upstream would run against a live tool now asks you for the input instead: paste the ticket, upload the CSV, describe the deal, share the doc.

## Making them yours

Fork and edit the markdown. That is the customization:

- Edit skill files to match your terminology, process, and policy
- Add company context (org chart, product names, playbooks) directly in `skills/`
- Create new plugins from the same layout or via `cowork-plugin-management`

## Upstream

Original: https://github.com/anthropics/knowledge-work-plugins (Apache 2.0). This fork tracks upstream and periodically syncs skills, with connector files omitted.

## Contributing

Plugins are just markdown. Fork, edit, and open a PR.
