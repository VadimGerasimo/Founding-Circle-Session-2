# Workshop Skills for Claude Code

Three ready-to-use skills for a hands-on Claude Code session. Unzip or clone, drop the
`.claude` folder into a Claude Code project, restart, and go.

| Skill | What it does | Trigger |
|---|---|---|
| **competitive-battlecard** | Builds a sales-ready battlecard vs a named competitor — positioning, feature table, objection handling, landmines, win/loss patterns. | `/competitive-battlecard` |
| **competitor-analysis** | Maps the competitive landscape, profiles competitors, surfaces differentiation. | `/competitor-analysis` |
| **caveman** | Strips filler from prose answers (~65–75% fewer output tokens), keeps code/errors intact. Fun, fast to demo. | `/caveman` (off: "normal mode") |

It also ships the **hands-on build commands** for the lead-qualification pipeline. Run
them in order — each one interviews you with a few questions, writes one piece of the
pipeline, and points you to the next:

1. `/build-icp` — write your scoring criteria (`ICP.md`)
2. `/build-skill` — the playbook that scores one lead against the ICP
3. `/build-qualifier-agent` — the worker that runs the skill
4. `/build-researcher-agent` — the worker that researches a bare company from the web
5. `/build-qualify-command` — the `/qualify` button that runs the whole loop

`leads.csv` at the root is the seed list. Enrichment happens **live during the session** when
you run the `/qualify` pipeline — that's the payoff, so the leads ship un-enriched on purpose.

---

## Install

### Option A — Download (no Git needed)

1. Click the green **Code** button above → **Download ZIP**, then unzip.
2. Copy the `.claude` folder into the **root of your Claude Code project**.
   If the project already has `.claude/skills/`, copy the three skill folders into it instead.
3. Start (or restart) Claude Code and type `/` to see them.

### Option B — Clone

```bash
git clone <REPO_URL>
# then copy the .claude folder into your project root
```

Final layout must look exactly like this — no extra nested folder:

```
your-project/
├── leads.csv
└── .claude/
    ├── commands/
    │   ├── build-icp.md
    │   ├── build-skill.md
    │   ├── build-qualifier-agent.md
    │   ├── build-researcher-agent.md
    │   └── build-qualify-command.md
    └── skills/
        ├── competitive-battlecard/SKILL.md
        ├── competitor-analysis/SKILL.md
        └── caveman/SKILL.md
```

---

## Gotcha (the #1 install error)

`SKILL.md` must sit **directly** inside its skill folder
(`.claude/skills/caveman/SKILL.md`), not double-nested
(`.claude/skills/caveman/caveman/SKILL.md`). If a skill doesn't appear, check the path,
confirm the filename is exactly `SKILL.md`, and start a fresh Claude Code session.

---

## Verify

In a Claude Code session ask: **"What skills do you have available?"** — all three should be listed.

---

## Credits & License

These skills are redistributed under the MIT License. Originals:

- **competitive-battlecard**, **competitor-analysis** — Paweł Huryn, https://github.com/phuryn/pm-skills
- **caveman** — Julius Brussee, https://github.com/JuliusBrussee/caveman

Full license texts in [`licenses/`](licenses/).
