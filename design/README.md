# Design Plugin

A design productivity plugin primarily designed for [Cowork](https://claude.com/product/cowork), Anthropic's agentic desktop application — though it also works in Claude Code. Helps with design critique, system management, UX writing, accessibility, research synthesis, and developer handoff. Works with any design team — standalone with your input, supercharged when you connect Figma and other tools.

## Installation

```bash
claude plugins add knowledge-work-plugins/design
```

## Commands

Explicit workflows you invoke with a slash command:

| Command | Description |
|---|---|
| `/critique` | Get structured design feedback — usability, visual hierarchy, accessibility, and consistency |
| `/design-system` | Audit, document, or extend your design system — components, tokens, patterns |
| `/handoff` | Generate developer handoff specs — measurements, tokens, states, interactions, and edge cases |
| `/ux-copy` | Write or review UX copy — microcopy, error messages, empty states, onboarding flows |
| `/accessibility` | Run an accessibility audit — WCAG compliance, color contrast, screen reader, and keyboard navigation |
| `/research-synthesis` | Synthesize user research — interviews, surveys, usability tests into actionable insights |

All commands work standalone (describe your design or paste screenshots).

## Skills

Domain knowledge Claude uses automatically when relevant:

| Skill | Description |
|---|---|
| `design-critique` | Evaluate designs for usability, visual hierarchy, consistency, and adherence to design principles |
| `design-system-management` | Manage design tokens, component libraries, and pattern documentation |
| `ux-writing` | Write effective microcopy — clear, concise, consistent, and brand-aligned |
| `accessibility-review` | Audit designs and code for WCAG 2.1 AA compliance |
| `user-research` | Plan, conduct, and synthesize user research — interviews, surveys, usability testing |
| `design-handoff` | Create comprehensive developer handoff documentation from designs |

## Example Workflows

### Getting Design Feedback

```
/critique
```

Share a Figma link, screenshot, or describe your design. Get structured feedback on usability, visual hierarchy, consistency, and accessibility.

### Auditing Your Design System

```
/design-system audit
```

I'll review your component library for consistency, completeness, and naming conventions. Get a report with specific improvement recommendations.

### Writing UX Copy

```
/ux-copy error messages for payment flow
```

Get context-appropriate copy with tone guidance, alternatives, and localization notes.

### Developer Handoff

```
/handoff
```

Share a Figma link and get a complete spec: measurements, design tokens, component states, interaction notes, and edge cases.

### Accessibility Check

```
/accessibility
```

Share a design or URL. Get a WCAG 2.1 AA compliance report with specific issues, severity, and remediation steps.

### Synthesizing Research

```
/research-synthesis
```

Upload interview transcripts, survey results, or usability test notes. Get themes, insights, and prioritized recommendations.

