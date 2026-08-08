---
name: handle-complaint
description: Handles an incoming customer complaint end-to-end — gathers context from the owner, drafts a response, and suggests an operational fix.
allowed-tools: Read, WebFetch, Bash
---

Run the complaint resolution workflow. Read the complaint, gather context, draft a response, and suggest a fix so it doesn't happen again.

Parse arguments:
- If the owner provides a complaint (pasted text, email, or ticket), work from it. If omitted, ask the owner to paste the complaint text.

## Step 1 — Load the complaint

1. Ask the owner to paste the complaint text (or the full email/ticket thread).
2. Identify: customer name, order/account info, what they're upset about, what they're asking for.

## Step 2 — Gather context

Ask the owner for anything they have on the customer:
1. Customer history: past purchases, prior complaints, deal stage, lifetime value (from their CRM or memory).
2. Transaction info: order status, refund history, dispute status (from their payment processor).
3. Summarize: "This is a {new/returning} customer, ${lifetime_value} in purchases, {0/N} prior complaints. Their current issue is {one sentence}." If context is unavailable, note that and work from the complaint text alone.

## Step 3 — Draft response

Draft a tone-matched reply:
1. Draft a reply matched to the severity and the customer's history:
   - First-time complainers with high LTV → empathetic, generous
   - Repeat complainers → professional, firm, solution-focused
   - Abusive tone → professional, brief, boundary-setting
2. Include: acknowledgment, explanation (if known), resolution offer, next step.
3. Present the draft to the owner. Do NOT send.

## Step 4 — Suggest operational fix

1. Ask the owner whether similar complaints have come up recently (or check notes from prior complaint-handling sessions).
2. If it's a pattern: "This is the {Nth} complaint about {issue} this month. Consider: {specific operational change}."
3. If it's isolated: "This looks like a one-off. No pattern detected."

## Missing data

If the owner has no complaint text, ask them to paste it — the skill works with manual input. If transaction or history context is unavailable, note "order status unavailable — working from complaint text only."

## Approval gates

- **Never send a response without explicit owner approval.** Drafts only.
- **Never issue refunds or credits automatically.** Present the option; the owner decides.
- **Never close tickets or resolve disputes without owner confirmation.**

## Output

Present the customer context summary, the drafted response, and any pattern-based operational suggestion. Ask: "Want to send this response, edit it, or handle it differently?"
