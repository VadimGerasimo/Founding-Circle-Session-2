---
description: Build your ICP file by answering a few questions. Writes ICP.md — the criteria every lead is scored against.
argument-hint: "(no args — just run it)"
---

# Build the ICP

You are guiding a non-technical commercial leader to create their **ICP** (Ideal
Customer Profile). The ICP is the one knob that steers every score in the pipeline:
the lead-qualifier skill reads it, so changing it changes every result.

**Teach it in one line, then start:** *"An ICP is just who you are and who you sell to —
the checklist every lead gets scored against. Answer 8 quick questions and I'll write it
into a file your tools will use."*

## How to run the interview
- Ask the **questions below ONE AT A TIME**. Wait for each answer before the next.
- This file is **their** scoring criteria — get their real answer to every question.
  The brackets show an **example** so they can see the shape; they are a fallback, not a
  recommendation. Nudge them to give their own; press enter only if an example genuinely
  fits their business. (Answering "default" to all still yields a working file.)
- Keep your acknowledgements to one short line. Do not lecture.

## Questions
*(Q1–Q2 are about **you** — the seller. They give the qualifier context for fit and for
writing openers. Q3–Q8 describe the **target**.)*
1. **What's your company name?** [Northwind Outreach]
2. **What do you offer, and what's your edge — one line?** [AI lead-qualification for sales teams; cuts research from ~40 min to seconds per lead]
3. **Who do you sell to, in one line?** [commercial / sales teams at B2B SaaS companies]
4. **Company size range that fits best?** [200–2000 employees]
5. **Which geographies?** [EU / UK]
6. **One thing a good-fit company must have?** [a field sales team]
7. **What signal means "reach out now"?** [recent funding, hiring spree, launch, or leadership change]
8. **One disqualifier that rules a company out?** [already runs an incumbent of type X]

**Then one last, optional question:**
> **Anything else the scorer should factor in?** *(optional — press enter to skip)*

If they answer, capture it verbatim into a **`## Notes / extra criteria`** section. If
they skip, **omit that section entirely** — don't write an empty heading.

## After the answers — write the file
Write their answers into **`ICP.md`** at the project root, in this exact shape
(fill the bracketed slots with their answers; keep the scoring rule verbatim):

```markdown
# ICP — Ideal Customer Profile

The scoring criteria the **lead-qualifier skill** reads. Change this file and every
score changes — it is the one knob that steers the whole pipeline.

## Us
- **Company**: {answer 1}
- **What we offer / our edge**: {answer 2}

## Who they are
- **Type / who we sell to**: {answer 3}
- **Size**: {answer 4}
- **Geography**: {answer 5}
- **Must have**: {answer 6}

## Buy-now signal (at least one)
{answer 7}

## Disqualifier
{answer 8}

## Notes / extra criteria
{the optional answer — include this whole section ONLY if they gave one}

## Scoring rule
- Fit is 0–100 against the points above.
- **No score above 60 without at least two confirmed ICP matches.**
- Unknown ≠ match. Missing data caps the score; it never invents a fit.
```

## When done — summarise what they built
After writing the file, show this short summary (adapt wording, keep it tight):

> **You built: `ICP.md`** — your scoring criteria, the one knob.
> **How it fits:** the lead-qualifier skill reads this file; every lead's score traces back to it. Change this → every score changes.
> **Pipeline so far:** `ICP.md` ✅ → skill → qualifier agent → /qualify → board.
> **Next:** `/build-skill` — the playbook that scores against your ICP.
