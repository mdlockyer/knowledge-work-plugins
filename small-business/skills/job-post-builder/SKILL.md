---
name: job-post-builder
description: >
  Builds end-to-end hiring packets — job post, structured interview guide with
  scoring rubric, and offer letter template — from a hiring brief. Triggers on:
  "help me hire", "we're hiring for", "write a job post", "job description",
  "JD", "open role", "create a job ad", "interview questions", "scoring rubric",
  "draft an offer letter", "send an offer", "make a hiring packet", or any
  request to recruit for a position. When in doubt, trigger — covers the full
  hiring workflow from job post through offer letter. Does NOT screen or rank
  applicants.
---

# Job Post Builder

Produces a complete hiring packet — job post, interview guide, and offer letter
— from a brief conversation about the role.

---

## Quick start

Invoke when a user says they need to hire someone or produce any hiring document.
The skill walks a 6-phase workflow: gather context → research the market → write
the job post → draft the interview guide → assemble the offer letter → deliver it.

**Example trigger:**
> "We're hiring a senior product manager. Can you put together the job post and
> interview questions?"

---

## Workflow

1. **Gather role context** — Ask for role title, responsibilities, qualifications,
   location, comp, interview process, and offer letter delivery preference.
   Source: conversation / AskUserQuestion.
2. **Research comparable posts** — Ask if there's a prior JD or template to use
   as a starting point; run web search for 3–5 live postings for this role.
   Sources: user files, web search.
3. **Write the job post** — Draft a market-informed job description using
   `references/job-post-structure.md`. Output: `[Role]-Job-Post.docx` via docx skill.
4. **Draft interview guide + scoring rubric** — Build a stage-by-stage guide using
   `references/interview-guide-structure.md`. Output: `[Role]-Interview-Guide.docx`
   via docx skill.
5. **Assemble offer letter** — Build offer letter with bracketed placeholders using
   `references/offer-letter-template.md`. Output: `[Role]-Offer-Letter.docx` via
   docx skill.
6. **Deliver the offer letter** — Save the letter as a .docx for the owner to
   review and send. If they want to send it via an e-signature service (e.g.
   DocuSign), guide them through uploading it in their browser — do not send
   anything on their behalf.

---

## Approval gates

- **Never send anything on the owner's behalf.** The offer letter is delivered as
  a .docx; sending (email, DocuSign, or otherwise) is the owner's job.
- **Never publish the job post.** Produce the .docx file only. Posting to any job
  board is the user's responsibility.

---

## Phase 1 — Understand the Role

Before researching or writing anything, gather enough context to do it well.
Ask the user (via conversation or AskUserQuestion) for:

- **Role title** — exact title they want to post
- **Team / function** — who this person reports to and works with
- **Key responsibilities** — 3–5 things this person will own day-to-day
- **Must-have qualifications** — hard requirements (years of experience, specific skills, credentials)
- **Nice-to-have qualifications** — preferred but not required
- **Location / remote policy** — on-site, hybrid, or fully remote; location if relevant
- **Compensation range** — salary band if they have one (flag that this needs HR/legal sign-off)
- **Existing JD or template?** — ask if there's a prior version they can share to use as a starting point
- **Offer letter delivery preference** — ask how they'd like the offer letter delivered:
  - *Word doc only* — skill saves the offer letter as a .docx and stops there; the user handles sending
  - *Help preparing to send* — skill produces the .docx and walks through uploading it to an e-signature service (e.g. DocuSign) in their browser

- **Interview process** — ask how their hiring process is structured:
  - How many rounds/stages are there?
  - Who conducts each stage? (e.g. recruiter, hiring manager, peer, skip-level, panel)
  - What is each stage meant to assess? (e.g. culture fit, technical depth, cross-functional collaboration)
  - Is there a take-home exercise or work sample at any stage?

  This is critical — the interview guide will be organized by stage, and each stage
  gets its own question set. If the user doesn't know yet, suggest a sensible default
  based on the role level and company size, and confirm before proceeding.

  Example default for a mid-senior IC role:
  | Stage | Interviewer | Focus |
  |---|---|---|
  | Phone screen | Recruiter | Communication, baseline fit, logistics |
  | Hiring manager interview | HM | Scope, ownership, role-specific depth |
  | Peer interview | Team member | Collaboration, working style |
  | Skills/case exercise | Senior IC | Relevant technical or domain depth |
  | Final / culture interview | Skip-level or exec | Values, long-term trajectory |

Capture the delivery preference in Phase 1 so the right Phase 5/6 path is clear
before any writing starts. If the user already indicated a preference, extract
it from their message rather than asking again.

If the user has already provided most of this in their message, extract it and
confirm before moving on rather than asking redundant questions. One focused
clarifying question is better than a long form.

---

## Phase 2 — Research Comparable Posts

Good job posts are grounded in what the market actually says for this role.
Do both of the following in parallel:

**A. Check existing files first**
Search Google Drive and Desktop for prior JDs, offer letter templates, or
interview guides the user may already have. Use file search tools with terms like
the role title, "job description", "JD", "offer letter", "interview". If found,
read them and use them as the baseline — preserving any existing language,
structure, or requirements the user has established.

**B. Web search for comparable posts**
Search for current job postings for this role at comparable companies. Good
sources include LinkedIn, Greenhouse, Lever, Workday, and company career pages.
Look for 3–5 real postings and note:
- Common responsibilities listed for this role
- Qualifications that appear consistently (these are table stakes)
- How companies describe the role's impact/scope
- Any language patterns that make postings feel compelling vs. generic

Use this research to pressure-test the user's requirements (are they missing
something standard? asking for something unusual?) and to make the job post
feel current and market-aware.

---

## Phase 3 — Write the Job Post

Read `references/job-post-structure.md` for the full recommended structure and
writing guidance.

**If an existing job post or JD was found in Phase 2:**
Use it as the structural template — mirror its section names, tone, ordering, and
any boilerplate the user has established (e.g. company description, benefits blurb,
how-to-apply language). The user's format is the source of truth.

Compare it against `references/job-post-structure.md` and surface any missing
components in a single question before writing:

> "Your existing JD has a responsibilities section and requirements list, but I
> didn't see an opening hook or a description of what success looks like in year one.
> Want me to add those, or keep it to your current format?"

Only add the missing components if the user confirms.

**If no existing job post was found:**
Build from scratch using `references/job-post-structure.md` as the full template.

**Either way:**
- Lead with impact, not just tasks
- Be honest about what's hard — candidates who self-select in are better fits
- Use inclusive language; avoid jargon that implicitly filters for in-group candidates
- Keep the required qualifications list tight — every line is a reason someone doesn't apply
- If compensation isn't provided, omit the range rather than invent one

Save as `[Role]-Job-Post.docx` using the docx skill.
Read `docx/SKILL.md` before generating the file.

---

## Phase 4 — Draft Interview Questions + Scoring Rubric

Read `references/interview-guide-structure.md` for the full recommended format.

**If an existing interview guide was found in Phase 2:**
Use the user's existing guide as the structural template — mirror its section names,
ordering, and formatting conventions. The user's format is the source of truth; the
reference file is a checklist, not an override.

After mapping the existing guide's sections against the reference, surface any
components present in the reference but missing from the user's guide. Present
these as a short, friendly question before writing — for example:

> "Your existing guide has a question bank and scoring rubric, but I noticed it
> doesn't include an interview stage map or a debrief guide. Want me to add those,
> or keep it to your current structure?"

Only add the missing components if the user confirms. Don't silently expand their
format without asking.

**If no existing guide was found:**
Build the guide from scratch using `references/interview-guide-structure.md` as
the full template. The reference defines the recommended sections, question format,
rubric anchors, and debrief guidance — follow it completely.

**Either way, organize the guide by interview stage using the process captured in Phase 1.**

Structure the document so each stage is its own section:

Each stage gets its own section with the stage name and interviewer as the heading,
followed by: the focus area this stage assesses, 4-6 behavioral questions specific
to that focus, 2-3 follow-up probes per question, and a 1/3/5 scoring rubric with
anchors for each competency the stage owns.

**Key principles for multi-stage guides:**
- Each competency should be owned by one stage — avoid two interviewers asking
  the same thing. If there's overlap, assign different angles.
- For panel interviews, split questions across panelists explicitly so each person
  knows what they're covering.
- If there's a take-home exercise, include a structured debrief section for
  reviewing it — what to look for, how to score it, follow-up questions.
- The debrief guide goes at the end, after all stage sections.
- 1/3/5 scoring anchors should be written for this specific role, not generic.

Save as `[Role]-Interview-Guide.docx` using the docx skill.

---

## Phase 5 — Assemble the Offer Letter Template

Read `references/offer-letter-template.md` for the full base template and field
definitions.

**If an existing offer letter or template was found in Phase 2:**
Use it as the structural template — preserve the user's formatting, clause ordering,
signature blocks, and any legal language they've already established. Their version
is the source of truth.

Compare it against `references/offer-letter-template.md` and surface any missing
components in a single question before writing:

> "Your existing offer letter has compensation and position details, but I noticed
> it doesn't include an at-will employment clause or a legal review disclaimer.
> Want me to add those, or keep it to your current format?"

Only add the missing components if the user confirms.

**If no existing offer letter was found:**
Build from scratch using `references/offer-letter-template.md` as the full template.

**Either way:**
- Use clearly marked `[BRACKETED]` placeholder fields for all candidate-specific values
- Include: at-will clause (if applicable), contingency conditions, legal review disclaimer
- Don't invent compensation figures — leave them as placeholders if not provided

Save as `[Role]-Offer-Letter.docx` using the docx skill.

**Then branch based on the delivery preference captured in Phase 1:**
- If the user wants help preparing to send via e-signature → proceed to Phase 6
- If the user chose **Word doc only** → skip Phase 6, deliver the .docx and close out

---

## Phase 6 — Prepare the Offer Letter for Sending

If the user wants to send the offer via an e-signature service (e.g. DocuSign),
walk them through it — do not operate the service on their behalf.

1. Deliver the `[Role]-Offer-Letter.docx` file.
2. Guide the user: "Upload this to DocuSign (or your e-signature tool), add the
   candidate as signer, and review the signature placement before sending."
3. Offer a ready-to-use message for the send:
   > "Hi [Candidate First Name], we're thrilled to extend this offer and look
   > forward to having you join the team. Please review and sign at your
   > earliest convenience. Don't hesitate to reach out if you have any questions."
4. If the user prefers email, draft the email with the letter attached and show
   it to them — they send it from their own email client.

---

## Delivering the Packet

Once all three files are created, present them together:

Present a summary listing the three deliverables by role title: the job post
docx (ready to post), the interview guide docx (share with interviewers), and
the offer letter docx (ready for the owner to review and send).

Remind the user:
- The offer letter template needs legal review before use in any jurisdiction
- Compensation ranges should be confirmed with HR before publishing the job post
- This skill does not screen or rank applicants

---

## Reference Files

Load these when reaching the relevant phase — don't load all upfront:

| File | Load when |
|---|---|
| `references/job-post-structure.md` | Phase 3 — before writing the job post |
| `references/interview-guide-structure.md` | Phase 4 — before writing the interview guide |
| `references/offer-letter-template.md` | Phase 5 — before writing the offer letter |
| `references/gotchas.md` | Any phase — non-obvious edge cases |
| `references/examples/worked-example.md` | For reference on expected output shape |

---

## Tests

See `tests/triggers.md` for must-trigger, must-NOT-trigger, and ambiguous routing cases.

See `tests/scenarios.md` for end-to-end scenario walkthroughs covering the happy
path and approval gate flows.
