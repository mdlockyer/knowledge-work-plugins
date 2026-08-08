# Small Business Plugin

Small business workflows for [Cowork](https://claude.com/product/cowork), Anthropic's agentic desktop application — also works in Claude Code. Building-block skills for the everyday work of running a small business: hiring, contracts, pricing, cash flow, and customer handling.

You don't need to memorize anything. Just tell Claude what you need — "a customer is angry," "what should I charge?", "review this contract" — and it produces the right output. You provide the inputs (files, exports, or a description of the situation) and Claude does the work.

> **Important**: This plugin assists with small business workflows but does not provide financial, tax, legal, or HR advice. All outputs should be reviewed by you (and where appropriate, a qualified professional) before use.

## Installation

### Cowork

Install from [claude.com/plugins](https://claude.com/plugins/).

### Claude Code

```bash
claude plugin marketplace add anthropics/knowledge-work-plugins
claude plugin install small-business@knowledge-work-plugins
```

## How it works

Every skill takes the data **you** provide — a pasted complaint, an uploaded contract, a CSV export of sales or expenses — and applies a structured workflow to it. No external tools are connected; you are the data source. Where a skill references a tool you use (QuickBooks, PayPal, DocuSign, etc.), it means you share the relevant export or file from that tool, and Claude works from it.

## Skills

| Skill | What it does | What you provide |
|---|---|---|
| **job-post-builder** | Builds a complete hiring packet: job post, structured interview guide with scoring rubric, and offer letter template. | A hiring brief ("we're hiring a senior PM, $160–180k") |
| **contract-review** | Plain-English NDA/MSA/vendor contract review with risk flags, severity ratings, and a marked-up redline DOCX. | A contract file (PDF/DOCX) or pasted text |
| **review-contract** | Contract review with red-flag severity ratings and redline suggestions. | A contract file (PDF/DOCX) |
| **handle-complaint** | End-to-end complaint resolution: draft a tone-matched response and suggest an operational fix. | The complaint text (plus customer history if you have it) |
| **margin-analyzer** | Unit economics by product or service with inflation benchmarks and three pricing scenarios. | CSV exports or figures for revenue and costs |
| **price-check** | Margin-by-product table and three pricing scenarios so you can see the full picture before pricing. | CSV exports or figures for revenue and costs |
| **cash-flow-snapshot** | 30/60/90-day cash flow forecast with confidence bands and named risk flags. Chat summary + XLSX. | CSV export or figures for AR/AP and fixed costs |

## Customizing

These workflows are generic starting points. They become much more useful when you customize them for how your business actually works:

- **Add business context** — Drop your industry, products, customers, and processes into skill files so Claude understands your world.
- **Adjust thresholds** — Tune the alert thresholds in `cash-flow-snapshot` to match your scale.
- **Edit templates** — Adapt the job post, interview guide, offer letter, and pricing output formats to your business.

## License

Skills are licensed under Apache 2.0.
