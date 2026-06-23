---
description: Run the WHOLE loop over a folder of leads — research any bare leads first, then score every lead in parallel and build a scoreboard.
argument-hint: "[folder, default: leads/]"
---

# /qualify — the full-loop button

The **button**. Press it and it runs the whole pipeline: it figures out which leads
still need research, sends the **`lead-researcher`** to enrich those, then sends a
**team** of **`lead-qualifier`** agents to score them all, and builds the board.

Target folder: `$ARGUMENTS` (default `leads/`).

Do this:

1. **List** every file in the target folder (default `leads/`).
2. **Triage each lead — enriched or bare?**
   - **Enriched** = the file already carries the profile fields (size, sector,
     location, recent signals). Most pre-staged leads are enriched.
   - **Bare** = essentially just a company name + website, or missing those fields.
3. **Enrich the bare ones first.** For each *bare* lead — and only those — dispatch a
   **`lead-researcher`** agent (web) to research it and **write an enriched profile back
   to `leads/<company>.md`**. Skip enriched leads entirely: no web call, no wasted work.
   *(So if every lead is already enriched, this step does nothing and `/qualify` makes
   no web calls at all — a re-run only researches genuinely new leads.)*
4. **Score everything — every lead, every run.** Once all leads are enriched, **in
   parallel dispatch one `lead-qualifier` agent per lead**. Each follows the
   **lead-qualifier skill**, scores against `ICP.md`, and writes its scorecard to
   `out/<company>.html` (a small, self-contained, styled card). Scoring is cheap and
   makes **no web calls**, so always rescore all of them — **never skip scoring.** That's
   what lets a **changed `ICP.md` re-flow through every lead**: edit the knob, re-run,
   every score updates.
5. **Build** `out/index.html`: a sortable board, one row per lead (Company · Fit/100 ·
   Strongest signal · Biggest risk · Likely buyer), highest fit first, each row linking
   to its card.
6. **Write `out/results.csv`** — one row per lead with header
   `company,fit,strongest_signal,biggest_risk,likely_buyer,status` (status =
   `researched` / `scored` / `unknown`). A fresh snapshot of **this** run — a clean
   spreadsheet of every lead researched, qualified, and scored. *(Only the **research**
   step skips repeat work — already-enriched leads aren't re-researched. Scoring is never
   skipped.)*
7. **Print** a one-line summary: how many qualified, the top 3 by fit, and how many
   needed live research.

Keep each agent's work tiny and bounded. Use the cheap model. Only bare leads hit the
web. If a lead still can't be assessed, give it a row marked "unknown — needs: …"
(status `unknown` in the CSV).
