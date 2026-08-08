# Gotchas

## 1. Missing candidate details before sending

✗ **Bad:** The offer letter is ready, and only then Claude asks: "What's the candidate's email address?" or "What's their full legal name?"

✓ **Good:** Collect the candidate's full name and email in Phase 1 (or by the end of Phase 5) so the deliverable is complete. Ask only for what's genuinely missing.

**Why it matters:** Asking for basic details mid-flow makes the skill feel disorganized and forces the user to re-engage after the writing work is done.

---

## 2. Re-asking for context the user already provided

✗ **Bad:** The user says "we need to hire a senior PM, fully remote, $160–180k"
and Phase 1 asks for role title, location, and compensation anyway.

✓ **Good:** Extract role title, location, and compensation from the message, confirm
them in a single sentence, and ask only for the fields that are genuinely missing.

**Why it matters:** The skill explicitly requires "one focused clarifying question
rather than a long form." Redundant questions break trust and slow the workflow.

---

## 3. Silently expanding the user's existing format

✗ **Bad:** The user has a 3-section job post on file. Claude produces a 7-section
post based on `references/job-post-structure.md` without asking.

✓ **Good:** Map the user's existing format against the reference, identify missing
sections, and ask one question: "Your existing JD has X and Y — want me to add Z,
or keep your current format?"

**Why it matters:** The user's format is the source of truth. Overriding it silently
may conflict with internal HR or legal standards the user hasn't mentioned.

---

## 4. Inventing compensation figures

✗ **Bad:** No salary range was provided, so Claude writes "$120,000–$150,000 DOE"
in the job post or offer letter.

✓ **Good:** If compensation isn't provided, omit the range from the job post entirely.
In the offer letter, use `[ANNUAL SALARY — confirm with HR]` as a bracketed placeholder.

**Why it matters:** Inventing compensation figures creates legal and HR liability.
The skill's instructions are explicit: "Don't invent a range."
