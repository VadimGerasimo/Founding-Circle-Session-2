---
description: Build the /qualify command by answering a few questions. Writes the full-loop button — researches any bare leads, scores them all in parallel, builds a scoreboard.
argument-hint: "(no args — just run it)"
---

# Build the /qualify command

You are guiding a non-technical commercial leader to create a **command** — a saved,
named trigger. The metaphor: the bell on the desk. Press it and the whole team goes.
This one is the **full-loop button**: it checks which leads still need research, sends
the **lead-researcher** to enrich those, then sends a fleet of **lead-qualifier** agents
to score them all, and builds a board.

**Teach it in one line, then start:** *"A command is a button you press — `/qualify`.
This one runs the whole loop: it spots any lead that still needs research, researches it,
then scores every lead in parallel and assembles a board. Five questions."*

> This is the **last** piece — it orchestrates the two hires you already built. If
> `.claude/agents/lead-qualifier.md` (the scorer) or `.claude/agents/lead-researcher.md`
> (the researcher) is missing, run `/build-qualifier-agent` / `/build-researcher-agent`
> first — the command dispatches both by name. (If the researcher is somehow absent, the
> button still scores already-enriched leads; it just can't handle bare ones.)

## How to run the interview
- Ask **ONE AT A TIME**, default in brackets, "default"/"skip" accepts it. One-line acks.

## Questions
1. **Which folder of leads does it run over?** [leads/ (the default)]
2. **If a lead isn't enriched yet, what should the button do?** [Detect it (a bare name/website, missing the profile fields) and send the lead-researcher agent to research it first — only bare leads hit the web; enriched leads are scored straight away.]
3. **How should it score them?** [In parallel — dispatch one named lead-qualifier agent per lead, each scoring against ICP.md.]
4. **What's the final artifact?** [out/index.html — a sortable board, one row per lead (Company · Fit/100 · Strongest signal · Biggest risk · Likely buyer), highest fit first, each row linking to its card.]
5. **What should it print when done?** [A one-line summary: how many qualified, the top 3 by fit, and how many needed live research.]

## After the answers — write the file
Write to **`.claude/commands/qualify.md`**, filling slots from their answers. Keep the
named agents explicit (`lead-researcher` for bare leads, `lead-qualifier` for scoring) —
naming them is what wires the pipeline together:

```markdown
---
description: Run the WHOLE loop over a folder of leads — research any bare leads first, then score every lead in parallel and build a scoreboard.
argument-hint: "[folder, default: leads/]"
---

# /qualify — the full-loop button

The **button**. Press it and it runs the whole pipeline: research the leads that need
it, then send a team of `lead-qualifier` agents to score them all, and build the board.

Target folder: `$ARGUMENTS` (default `{answer 1}`).

Do this:
1. List every file in the target folder.
2. **Triage each lead — enriched or bare?** Enriched = already has the profile fields
   (size, sector, location, signals). Bare = essentially just a name + website.
3. **Research the bare ones first.** {answer 2} The lead-researcher writes an enriched
   profile back to `leads/<company>.md`. *(If every lead is already enriched, this step
   does nothing and the button makes no web calls.)*
4. **Score everything.** {answer 3} Each writes its scorecard to `out/<company>.html`
   (a small, self-contained, styled card).
5. When all workers finish, build the final artifact: {answer 4}
6. {answer 5}

Keep each agent's work tiny and bounded. Use the cheap model. Only bare leads hit the web.
If a lead still can't be assessed, give it a row marked "unknown — needs: …".
```

## When done — summarise what they built
After writing the file, show this short summary (adapt wording, keep it tight):

> **You built: `/qualify`** — the full-loop button, and the last piece. Press it, the whole pipeline runs.
> **How it fits:** it checks each lead — already enriched leads get scored straight away; bare ones get sent to the **lead-researcher** first, then scored. One `lead-qualifier` agent per lead, in parallel, against your `ICP.md`, then a sortable board. **This is where all five pieces combine into one press.**
> **Pipeline COMPLETE:** ICP ✅ → skill ✅ → qualifier hire ✅ → researcher hire ✅ → `/qualify` ✅ → board.
> **Run it now (the climax):** **`/qualify`** on the pre-staged `leads/` — they're already enriched, so it scores them with **no web calls**: your whole pipeline working end-to-end.
> **The full live loop — same button:** drop a **bare company name + website** into `leads/` and run `/qualify` again. It spots the bare one, researches it live, then scores it — the 40-minutes-per-lead of manual research, gone. You built all of it by answering questions.
