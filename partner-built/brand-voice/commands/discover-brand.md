---
description: Collect brand materials from the user and produce a discovery report
argument-hint: "[company name]"
---

Collect the user's brand materials — style guides, decks, templates, transcripts — and produce a discovery report that feeds guideline generation. Works entirely from materials the user shares: file uploads, pasted text, or links.

If $ARGUMENTS includes a company name, use it to ground the discovery report.

Before doing anything else, briefly orient the user on what's about to happen: you'll collect their brand materials, produce a discovery report, and then (optionally) generate and save brand guidelines to `.claude/brand-voice-guidelines.md` in the working folder. Nothing is saved until they explicitly approve. Keep the orientation to 2-3 sentences — don't recite the full workflow.

Follow the discover-brand skill instructions to:
1. Check `.claude/brand-voice.local.md` for settings (company name, known material locations)
2. Collect materials across the useful categories (official docs, sales/marketing content, customer-facing comms, conversational samples, design materials)
3. Triage and rank sources by value for brand voice
4. Produce the structured discovery report with sources, brand elements, conflicts, and open questions
5. Offer next steps: generate guidelines, resolve open questions, or save the report

**Coverage guidance:**
- If the user has nothing to share, ask for whatever they have — even one deck or a few emails — or offer to work from a verbal description of their brand voice.
- If materials are sparse (a single source), note that confidence scores will be lower and recommend collecting more before generating guidelines.
- If sources conflict (old style guide vs. new brand direction), surface the conflict as an open question rather than picking a winner silently.
