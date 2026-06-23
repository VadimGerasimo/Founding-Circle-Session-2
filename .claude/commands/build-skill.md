---
description: Build the lead-qualifier skill by answering a few questions. Writes the SKILL.md playbook that scores ONE enriched lead against your ICP.
argument-hint: "(no args — just run it)"
---

# Build the lead-qualifier skill

You are guiding a non-technical commercial leader to create a **skill** — the *how-to*,
the playbook, written once and shared. Here it scores ONE company against the ICP.

**Teach it in one line, then start:** *"A skill is a job description you write once —
the playbook your AI workers follow. We're writing the one that scores a single lead.
It reads the ICP.md you just made. Answer 4 questions."*

> If `ICP.md` does not exist yet, tell them to run `/build-icp` first — the skill scores
> against it.

## How to run the interview
- Ask the **questions below ONE AT A TIME**. Brackets show an **example**, not the answer
  to accept. This skill is the **voice** of their scorer — its persona, what each
  scorecard emphasises, its hard rules — so get their own take; that's what makes the
  build theirs. Enter accepts the example (all-examples still yields a working skill).
- One-line acknowledgements. No lecturing.

## Questions
1. **What's the one-company job, in a sentence?** [Qualify and score one company against our ICP and prep the first outreach.]
2. **What persona should the analyst take?** [A precise, skeptical B2B lead-qualification analyst who never invents facts.]
3. **What should each scorecard contain?** [Fit 0–100, top 3 reasons, strongest signal, biggest risk, likely buyer, a 2-sentence opener.]
4. **Any hard rules it must never break?** [Never invent facts; unknown = "unknown" + what's needed; no score above 60 without two confirmed ICP matches; openers stay human and specific.]

**Then one last, optional question:**
> **Anything else this playbook should always do?** *(optional — press enter to skip)*

If they answer, append it verbatim as an extra bullet under `## GUARDRAILS`. If they
skip, leave the guardrails as the default below.

## After the answers — write the file
Write to **`.claude/skills/lead-qualifier/SKILL.md`** (create the folder if needed),
filling the slots from their answers. Keep the structure exactly — the INPUT/METHOD
wiring is what makes the pipeline work, so do **not** add a research step:

```markdown
---
name: lead-qualifier
description: Qualify and score ONE company against our ICP from an enriched profile. Reads ICP.md. Produces a fixed scorecard. Research is the lead-researcher agent's job, upstream.
---

# Lead Qualifier

{answer 1}
This is the playbook (the "skill"). A command fans it out across many leads; an agent
is the worker that runs it. You just do one well.

## ROLE
{answer 2}

## INPUT
One company as an **enriched profile** (research already done upstream by the
lead-researcher agent — see `leads/`). You score what you're handed; you do not research.
Missing field = "unknown". The criteria you score against live in **`ICP.md`** — read it.

## METHOD
1. Read **`ICP.md`** for the current scoring criteria.
2. Extract what is knowable from the profile: size, sector, location, recent signals.
3. Score fit 0–100 against the ICP. Give the 3 biggest reasons.
4. Flag the single strongest buying signal and the single biggest risk/disqualifier.
5. Name the likely economic buyer (role/title) and a probable trigger.
6. Draft a 2-sentence opener referencing one specific, real detail — and tie it to our
   offer / edge from the **`## Us`** block in `ICP.md`.

## OUTPUT
A single scorecard: {answer 3}. Keep it to one compact card. If you cannot assess the
company, say so and list exactly what information you would need.

## GUARDRAILS
{answer 4}
```

## When done — summarise what they built
After writing the file, show this short summary (adapt wording, keep it tight):

> **You built: the `lead-qualifier` skill** — the playbook, written once and shared.
> **How it fits:** it reads `ICP.md`; an agent will follow it; a command will run it across many leads. It's the bottom of the stack — everything points down to it. It scores; it does not research.
> **Pipeline so far:** ICP ✅ → skill ✅ → qualifier agent → /qualify → board.
> **Next:** `/build-qualifier-agent` — the worker (the "hire") that runs this skill.
