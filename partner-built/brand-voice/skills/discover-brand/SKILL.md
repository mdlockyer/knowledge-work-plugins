---
name: discover-brand
description: >
  This skill orchestrates discovery of brand materials from whatever the user
  provides — files, pasted documents, links, and transcripts. It should be used
  when the user asks to "discover brand materials", "find brand documents",
  "audit brand content", "what brand materials do we have", "find our style guide",
  "do we have a style guide", "discover brand voice", "brand content audit",
  or "find brand assets".
---

# Brand Discovery

Gather brand materials from the user, triage them, and produce a structured discovery report with open questions. Works entirely from materials the user shares — files, pasted text, or links.

## Discovery Workflow

### 0. Orient the User

Before starting, briefly explain what's about to happen so the user knows what to expect:

"Here's how brand discovery works:

1. **Collect** — You share your brand materials: style guides, pitch decks, templates, email samples, transcripts, and anything else that shows how your company communicates.
2. **Analyze** — I'll categorize and rank what you give me, pull out the strongest signals, and produce a discovery report with what I found, any conflicts, and open questions.
3. **Generate guidelines** — Once you've reviewed the report, I can generate a structured brand voice guideline document from the results.
4. **Save** — Guidelines are saved to `.claude/brand-voice-guidelines.md` in your working folder once you approve them. Nothing is written until that step."

### 1. Check Settings

Read `.claude/brand-voice.local.md` if it exists. Extract:
- Company name
- Any known brand material locations
- Search depth preference

If no settings file exists, proceed with what the user provides.

### 2. Collect Materials

Ask the user for brand materials. Useful categories:

- **Style guides / brand books** — official voice, tone, and visual rules
- **Marketing collateral** — website copy, pitch decks, product pages, ads
- **Sales materials** — email templates, proposals, LinkedIn posts, sales scripts
- **Customer-facing comms** — support responses, newsletters, announcements
- **Conversational samples** — call transcripts, meeting notes, Slack threads (show how the team actually talks)
- **Design system files** — color, typography, and design tokens (inform voice)

Accept materials in any form: file uploads (PDF, DOCX, MD), pasted text, or links to shared documents.

### 3. Triage and Rank Sources

Categorize each source and rank by value for brand voice:

1. **Official** — style guides, brand books, messaging frameworks (highest weight)
2. **Applied** — real customer-facing content produced by the team
3. **Conversational** — call transcripts, meeting notes, Slack threads (reveal implicit voice)
4. **Design** — design systems, visual identity docs

Note when sources conflict (e.g., a 2023 style guide vs. a 2024 rebrand) — flag these as open questions rather than picking a winner silently.

### 4. Produce the Discovery Report

Present a structured report:
- Total sources collected and analyzed
- Key brand elements discovered
- Any conflicts between sources
- Open questions requiring team input

### 5. Offer Next Steps

After presenting the report, offer:
1. **Generate guidelines now** — chain to `/brand-voice:generate-guidelines` using the discovery report as input
2. **Resolve open questions first** — work through high-priority questions before generating
3. **Save report** — store the discovery report as a local file
4. **Collect more** — accept additional materials if coverage is low

## Open Questions

Open questions arise when discovery encounters ambiguity it cannot resolve:
- Conflicting documents (e.g., 2023 style guide vs. 2024 brand update)
- Missing critical sections (e.g., no social media guidelines found)
- Inconsistent terminology across materials

Every open question includes a recommendation. Present questions as "confirm or override" — not dead ends.

## Integration with Other Skills

- **Guideline Generation**: Pass the discovery report directly to the guideline-generation skill as structured input, replacing the need for users to manually gather sources.
- **Brand Voice Enforcement**: Once guidelines are generated from discovery, enforcement uses them automatically.

## Error Handling

- If the user has no materials to share, suggest they upload whatever they have (even one deck or a few emails) or describe their brand voice verbally — discovery can work from a single strong source.
- If materials are sparse, flag the discovery as "low coverage" and note that confidence scores will be lower.
- If a file can't be read, ask the user to re-upload or paste the content.

## Reference Files

For detailed discovery patterns, consult:

- **`references/source-ranking.md`** — Source category definitions, ranking algorithm weights, and triage decision criteria
