---
description: Build your ICP file by answering a few questions. Writes ICP.md — the criteria every lead is scored against.
argument-hint: "(no args — just run it)"
---

# Build the ICP

You are guiding a non-technical commercial leader to create their **ICP** (Ideal
Customer Profile). The ICP is the one knob that steers every score in the pipeline:
the lead-qualifier skill reads it, so changing it changes every result.

**Teach it in one line, then start:** *"An ICP is just your 'who we sell to' — the
checklist every lead gets scored against. Answer 6 quick questions and I'll write it
into a file your tools will use."*

## How to run the interview
- Ask the **questions below ONE AT A TIME**. Wait for each answer before the next.
- Every question shows a **default** in brackets. If they say "default", "skip", or
  press enter, use the default. They can change any of it later.
- Keep your acknowledgements to one short line. Do not lecture.

## Questions
1. **What do you sell, and to whom in one line?** [B2B SaaS sold to commercial teams]
2. **Company size range that fits best?** [200–2000 employees]
3. **Which geographies?** [EU / UK]
4. **One thing a good-fit company must have?** [a field sales team]
5. **What signal means "reach out now"?** [recent funding, hiring spree, launch, or leadership change]
6. **One disqualifier that rules a company out?** [already runs an incumbent of type X]

## After the answers — write the file
Write their answers into **`ICP.md`** at the project root, in this exact shape
(fill the bracketed slots with their answers; keep the scoring rule verbatim):

```markdown
# ICP — Ideal Customer Profile

The scoring criteria the **lead-qualifier skill** reads. Change this file and every
score changes — it is the one knob that steers the whole pipeline.

## Who they are
- **Type / who we sell to**: {answer 1}
- **Size**: {answer 2}
- **Geography**: {answer 3}
- **Must have**: {answer 4}

## Buy-now signal (at least one)
{answer 5}

## Disqualifier
{answer 6}

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
