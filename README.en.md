# Presentation Report Preflight (Pre-Planning Skill for Reporting Decks)

> Before any PPT/HTML gets generated, figure out *how this talk should actually land*.
>
> This is an **upstream planning skill**: it doesn't draw slides. It turns a topic, a source document, an old deck, a PDF, raw data, or notes into a structured, handoff-ready **Presentation Strategy Brief**, which a downstream slide-generation skill then executes.

> 🇨🇳 中文版见 [README.md](./README.md)

---

## Install

This repo's root is a standard skill (it contains `SKILL.md`), installable in one line with the open-source [`skills` CLI](https://github.com/vercel-labs/skills) (works with Claude Code, Codex, Cursor, OpenCode, and more):

```bash
# Install into the current project
npx skills add archlizheng/presentation-report-preflight

# Install at the user level (global, available across projects)
npx skills add archlizheng/presentation-report-preflight -g

# Install for a specific agent (e.g. Codex / Claude Code)
npx skills add archlizheng/presentation-report-preflight -a codex
npx skills add archlizheng/presentation-report-preflight -a claude-code
```

The CLI detects the skill and copies files into the right agent's skills directory — no manual setup. Common management commands:

```bash
npx skills list          # list installed skills
npx skills update         # update all skills
npx skills remove presentation-report-preflight   # uninstall
```

> You can also `git clone` this repo and drop the whole directory into your skills folder (e.g. `~/.codex/skills/` or `~/.claude/skills/`).

---

## What problem it solves

Most "AI-made decks" fail not because they're ugly, but because **layout starts before thinking does**:

- Who's the audience, what should they *do*, what's the success criterion — undefined, yet work begins;
- Each slide title is a *topic* instead of a *conclusion*, so reading the titles end-to-end tells no story;
- Numbers have no source, no comparison baseline — sometimes they're fabricated;
- No timing plan, so the talk either overruns or runs dry on stage;
- Handed straight to a generator, the downstream skill is left guessing copy, charts, and assets.

This skill freezes those **upstream decisions** into a brief: scenario, audience, goal, narrative framework, timing strategy, conclusion-style title chain, per-page content blueprint (`content_spec`), evidence plan, speaker notes, Q&A risks, visual intent, constraints, and a **Universal Handoff Contract**. Any competent slide-generation skill can execute directly from it.

---

## Key features

| Capability | What it does |
| --- | --- |
| **Direction before content** | Lock scenario/audience/goal/timing before layout; pick a narrative framework before laying out pages. |
| **Conclusion-style title chain** | Every title is a standalone claim; read together they form the whole summary. |
| **Per-page content_spec** | Each page ships its message, on-slide copy, visual blueprint, data/asset references, and talking points — the downstream invents nothing. |
| **Tiered output (lite/full)** | A 5-minute standup gets the lite tier; an investor pitch or promotion defense gets the full tier — depth matched to stakes. |
| **Per-page spec_density** | A third axis beyond lite/full: core pages `full`, routine pages `compact`, so long decks don't blow up the contract. |
| **Provenance (source_status)** | Every evidence item is tagged `verified / user_reported / assumed / to_verify` — a self-reported or assumed number is never dressed up as verified. |
| **Runtime downstream resolution** | Downstream skill names are only examples; the actual target is matched against available skills at runtime, degrading to a universal contract if not found — never guessing private fields. |
| **Run mode** | `interactive` keeps confirmation gates; `autonomous` (headless / called by another skill) skips them, records assumptions, never blocks. |
| **Language decoupling** | Contract YAML keys stay English (machine-stable); the human-readable layer follows `output_language`. |
| **Machine-checkable contract** | A JSON Schema validates the contract's structure and enum values — not a prose-level convention. |
| **Weakest-link self-check** | Instead of "12 green checks," it names the 1–2 spots most likely to fail on stage, plus concrete fixes. |

---

## Repository structure

```
presentation-report-preflight/
├── SKILL.md                              # Main entry: rules, workflow, output format
├── agents/
│   └── openai.yaml                       # Interface metadata (display name, default prompt)
└── references/
    ├── scenario-playbooks.md             # Playbooks/structures/taboos for 12 reporting scenarios
    ├── narrative-frameworks.md           # 13 narrative frameworks + selection tree
    ├── data-viz-guide.md                 # Chart selection, number storytelling, color rules
    ├── content-spec-guide.md             # Per-page content blueprint schema and how-to
    ├── speaker-notes-template.md         # Speaker notes / pacing / Q&A templates
    ├── presentation-checklist.md         # Pre-delivery self-check (the single source of truth)
    ├── downstream-adapter-protocol.md    # Runtime downstream-skill resolution & degradation
    ├── handoff-contract.schema.json      # Machine-checkable JSON Schema for the contract
    └── example-brief.md                  # End-to-end example (full + lite, regression baseline)
```

> `references/` are loaded on demand — the "Reference routing" table in SKILL.md says which ones the current task needs; you never read them all at once.

---

## Workflow at a glance

```
Phase 0   Detect input / run_mode / downstream target / output language / tier
Phase 1   Infer without interrogation (don't ask what can be inferred; batch the essentials)
Phase 2   Load the scenario playbook (scenario-playbooks)
Phase 3   Pick the narrative framework (narrative-frameworks)
Phase 3.5 Direction + timing confirmation gate (interactive mode)
Phase 4   Build the conclusion-style title chain
Phase 4.5 Title-chain confirmation gate (two-beat delivery)
Phase 4.7 Per-page content_spec (content-spec-guide)
Phase 5   Data & evidence plan (with source_status)
Phase 6   Speaker notes & Q&A (speaker-notes-template)
Phase 7   Downstream handoff (universal contract + runtime-resolved adapter appendix)
Phase 8   Pre-delivery self-check (name the weakest link + schema validation)
```

---

## Deliverable: the Presentation Strategy Brief

A `presentation-strategy-brief.md` structured as:

1. **Summary (human-readable)** — one-line claim, what the audience should remember/do, recommended framework, timing strategy, status.
2. **Timing Brief** — total duration, talk/Q&A split, page count, pacing, compressed version, overrun risks.
3. **Slide Title Chain** — a table of per-page conclusion-style titles.
4. **Universal Handoff Contract (authoritative YAML)** — the machine-checkable single source of truth.
5. **Adapter-specific Appendix** — added only when a downstream skill is named *and* resolved at runtime.
6. **Pre-delivery self-check (weakest link)** — the 1–2 most likely failure points + fixes.

The human-readable layer comes first for the user to review; the authoritative YAML comes after for the downstream to execute.

### Validating the contract

The contract can be validated with the provided schema (needs `pyyaml` + `jsonschema`):

```python
import yaml, json, re
from jsonschema import Draft202012Validator

schema = json.load(open("references/handoff-contract.schema.json"))
brief  = open("presentation-strategy-brief.md").read()
contract = next(b for b in re.findall(r"```yaml\n(.*?)```", brief, re.S)
                if "brief_tier:" in b)
Draft202012Validator(schema).validate(yaml.safe_load(contract))
```

The `full` and `lite` tiers have different required fields; the schema validates each conditionally.

---

## How to use

Trigger it in a skill-aware environment, e.g.:

> Use presentation-report-preflight to turn this old deck / this topic / this source doc into a presentation strategy brief, then hand it to huashu-design to generate HTML.

The skill will infer direction and (in interactive mode) confirm it → show you the title chain to review → expand the full contract → point out the weakest link. If you want speed, add "just make it / don't ask" to skip the gates.

---

## Design principles

1. **Runtime resolution > hardcoding**: downstream names, language, and interactivity are decided at runtime, not baked into the prose.
2. **Single source of truth + checkable**: the self-check lives in one place; the contract is upgraded from prose convention to a machine-checkable schema.
3. **Make state explicit > implicit assumptions**: fabrication, missing data, and missing confirmation all become enum fields the model must fill — and that surface automatically.

---

## Where it fits

Sales proposals, investor pitches, product launches, annual/quarterly reviews, promotion defenses, project retrospectives, technical talks, training, consulting/strategy reports, internal weekly syncs, customer case studies — each has its own playbook and taboos in `scenario-playbooks.md`.

---

## License

MIT License, see [LICENSE](./LICENSE).
