---
name: presentation-report-preflight
description: Preflight planning skill before HTML/PPT deck generation. Use when the user wants to create, rewrite, convert, or strengthen a real report deck, sales proposal（销售提案）, investor roadshow（融资/路演）, product launch（产品发布）, promotion defense（晋升答辩）, consulting/strategy deck（咨询/战略汇报）, training（培训）, technical talk（技术分享）, retrospective（复盘）, case-study deck（客户案例）, or a downstream HTML PPT workflow handed to a slide-generation skill (e.g. `frontend-slides-editable`, `guizang-ppt-skill`, `huashu-design`, or any future skill — these are illustrative; the actual downstream is resolved at runtime against the available skills, never assumed to exist). Turns a topic, source document, old deck, PDF, data, or notes into a Presentation Strategy Brief with audience, scenario, goal, narrative framework, timing brief, conclusion-style title chain, page-level content_spec, evidence plan, speaker notes, Q&A risks, visual intent, constraints, universal handoff contract, and optional adapter appendix. Infer direction first, confirm direction and timing before generating the brief unless the user explicitly wants speed, and ask only essential batched questions.
---

# Presentation Report Preflight

## Objective

Create a `Presentation Strategy Brief` before any downstream slide-generation skill starts visual design, HTML implementation, animation, or export work. Make the presentation effective as a report, pitch, talk, defense, class, or decision artifact—not merely attractive.

This is an independent upstream skill. It does **not** generate the final HTML deck. It prepares direction, timing strategy, story, structure, page-level content blueprints, evidence, slide titles, speaker notes, Q&A risks, visual intent, constraints, and a handoff contract that downstream skills can execute.

## Core rules

1. Infer first: extract scenario, audience, objective, duration, source material, language, assets, and likely downstream target from the user's prompt and attached/source files before asking.
2. Confirm direction before brief: before building the slide title chain or full brief, show an inferred `Direction Snapshot` plus `Timing Brief` and ask for confirmation. Skip only when the user says “先出片”, “别问”, “直接给”, “just make it”, or clearly asks for immediate full output; in that case state the assumptions and continue.
3. Ask lightly: ask at most one batched clarification message only for missing items that would materially change the brief. Direction confirmation is not interrogation: it confirms the inferred reporting direction and timing, not a blank questionnaire.
4. Scene before style: decide reporting scenario, audience, desired action, success criteria, and timing strategy before discussing templates or layouts.
5. Story before slides: choose a narrative framework before planning pages. Treat the framework and title chain as negotiable drafts.
6. Time before detail: the timing plan determines depth, page count, section allocation, Q&A reserve, and which pages to cut if time is short.
7. Content before layout: for full briefs, every slide must include a page-level `content_spec` that defines the message, on-slide copy, visual blueprint, data refs, asset refs, narration, and constraints before downstream skills choose layout, animation, or implementation. Lite briefs use compact `content_spec` only where it prevents ambiguity.
8. Claims before topics: every slide title must be a conclusion-style claim, not a category label.
9. Evidence before decoration: every metric needs a unit, source, and comparison baseline. Do not invent facts, metrics, sources, customer names, case details, or ROI numbers.
10. One job per page: each slide must have one persuasion/teaching/decision task. Split overloaded pages.
11. Hook and close are mandatory: the first 30 seconds need a hook; the ending needs a CTA, decision request, or memorable takeaway.
12. Speaker notes are part of the deliverable unless the user opts out.
13. The YAML `Universal Handoff Contract` is the single source of truth. The summary, timing brief, and title-chain table are human-readable projections of it. But the human-readable layer is the primary interface the user reviews — never dump the full YAML at the user for sign-off before they have confirmed the direction and, for full-tier briefs, the title chain.
14. Always output the universal contract. Add an adapter appendix only when a downstream skill is named **and resolved at runtime**, and build it by reading that downstream skill's current instructions at runtime. The downstream names in this skill are examples only — never assume one exists, never hardcode private layout IDs, preset names, CSS classes, or DOM assumptions. Record what was requested vs. resolved in `adapter_resolution`.
15. Scale depth to stakes: the size of the brief must match the weight of the talk. Do not apply the full heavy structure to a low-stakes deck. Pick a `brief_tier` (lite/full) and produce only what that tier needs — over-producing a 5-minute standup with a full evidence/speaker/Q&A contract is the same failure mode as over-interrogating the user.
16. Provenance is explicit, not implied: every evidence item and metric carries a `source_status` of `verified | user_reported | assumed | to_verify`. You cannot verify truth, but you must always state the status. Never silently promote a `user_reported` or `assumed` number into something that looks `verified`. Any `assumed` / `to_verify` item must surface in the weakest-link self-check and in that page's `footnotes`.
17. Choose a run mode before the gates: detect `run_mode` (`interactive | autonomous`) in Phase 0. `interactive` keeps the confirmation gates; `autonomous` replaces every gate with "state assumptions, continue, record in `open_questions`" and never blocks. Decide by, in order: explicit user instruction → execution context (headless / called by another skill or workflow / no chance to reply) → speed keywords as a last-resort fallback.
18. Density is per-page, orthogonal to tier: each slide carries `spec_density` (`full | compact`). Core pages (hook / proof / case / cta, and any page with a key number or required asset) get `full`; routine pages get `compact`. For decks over ~20 slides, default to this hybrid even within `brief_tier: full` so the contract does not explode.
19. Decouple language from structure: contract YAML keys stay in English (machine-stable); the human-readable layer follows `output_language`. The Chinese section labels in this skill's templates are illustrative defaults for Chinese reporting — translate them when `output_language` differs.
20. Declare what you read: list the references actually consulted in `references_consulted` so reference-skipping is visible.

## Reference routing

Load only the references needed for the current task:

| Need | Read |
| --- | --- |
| Pick or explain a narrative structure | `references/narrative-frameworks.md` |
| Apply scenario-specific strategy | `references/scenario-playbooks.md` |
| Plan metrics, comparisons, charts, or KPI pages | `references/data-viz-guide.md` |
| Build page-level content blueprints, information graphics, image slots, on-slide copy, or downstream-ready page details | `references/content-spec-guide.md` |
| Draft speaker notes, timing, Q&A, or data口径 | `references/speaker-notes-template.md` |
| Final self-check and repair guidance | `references/presentation-checklist.md` |
| Resolve / adapt to a named downstream skill | `references/downstream-adapter-protocol.md` |
| Validate the handoff contract structure | `references/handoff-contract.schema.json` |
| Need a complete output model | `references/example-brief.md` |

## Workflow

### Phase 0 — Detect input, run mode, handoff mode, downstream target, language

Classify the task:
- new deck from a topic, notes, outline, or raw idea;
- deck from document, research, PDF, data, transcript, or source report;
- rewrite/upgrade an old PPT/PDF/HTML deck;
- strengthen story/logic before a downstream deck skill executes;
- strategy brief only.

Detect `run_mode` (see core rule 17):
- `interactive` — there is a real user who can answer; keep the Phase 3.5 and 4.5 gates.
- `autonomous` — headless run, invoked by another skill/workflow, or the user clearly wants no back-and-forth; skip gates, state assumptions inline, record unknowns in `open_questions`.
- Decide by priority: explicit instruction → execution context → speed keywords (“先出片”, “别问”, “直接给”, “just make it”) as the last-resort fallback only.

Detect `output_language` from the user's prompt and source material (default: the language the user is writing in). Contract YAML keys stay English; the human-readable layer and on-slide copy follow `output_language`.

Select handoff mode:
- `universal_only` when no downstream skill is specified, the target is unknown or cannot be resolved at runtime, or the user wants a portable brief;
- `universal_plus_adapter` when the user names one or more downstream skills **and** they resolve at runtime (see Phase 7 and `references/downstream-adapter-protocol.md`).

Recognize downstream targets from the user's words. The names `frontend-slides-editable`, `guizang-ppt-skill`, `huashu-design`, “HTML PPT skill” are examples — always confirm the named skill actually exists in the current environment before promising an adapter.

Select brief tier:
- `lite` when the deck is low-stakes or short: internal weekly sync/standup, a single training segment, status update, or any talk under ~10 minutes / under ~8 slides.
- `full` when the deck is high-stakes or longer: sales proposal, investor pitch, product launch, promotion defense, consulting/strategy, annual report, or any talk ~10 minutes or more.
- When ambiguous, default to `full`, state in one line why this tier was chosen, and tell the user they can switch with one word (e.g. “给我精简版/lite”).

Plan `spec_density` (see core rule 18): `brief_tier` sets the overall contract weight; `spec_density` is decided per slide. Mark core pages (hook / proof / case / cta, or any page carrying a key number or required asset) as `full`, routine pages as `compact`. For decks over ~20 slides, apply this hybrid even under `brief_tier: full` so the contract stays handoff-sized instead of exploding.

### Phase 1 — Discovery without interrogation

Infer these fields from provided material first:
- scenario: sales proposal, investor pitch, product launch, annual/quarterly report, promotion defense, retrospective, technical talk, training, consulting delivery, strategy report, internal sync, case study, etc.;
- audience: executives, customers, investors, judges, colleagues, learners, public, technical peers;
- desired action or decision;
- success criteria;
- duration or slide-count target;
- available source material, data, images, logo, brand assets, examples;
- language/locale;
- downstream skill preference and export/editability expectations.

Ask only if a missing field cannot be inferred and would change the story or contract. Batch all questions in one concise message. If speed is requested, continue without asking and mark unknowns in `open_questions`.

### Phase 2 — Scenario playbook

When the scenario is known, read `references/scenario-playbooks.md`. Use the closest playbook to determine the goal, recommended structure, must-have elements, visual implications, and taboos.

### Phase 3 — Narrative framework

When choosing or justifying structure, read `references/narrative-frameworks.md`. Recommend one primary framework and at most one auxiliary framework.

Default mapping:
- Sales proposal → Problem → Solution → Benefit.
- Investor pitch → Pitch Deck 10 pages or AI project roadshow 6 checks.
- Product launch → Hero's Journey + Sparkline.
- Annual/quarterly report → BARO or six-part review.
- Promotion defense（晋升答辩）→ promotion SOP + STAR/BARO.
- Retrospective → four-step review method.
- Technical talk → Why → What → How → Demo → Limitation.
- Training → What → Why → How → Practice → Check.
- Consulting/strategy → SCQA + Pyramid Principle.
- Internal weekly sync → Status → Blockers → Support.
- Case study → Background → Challenge → Solution → Results or PAST.

### Phase 3.5 — Direction and Timing Confirmation Gate

Before generating the slide title chain or full brief, produce a compact `Direction Snapshot` and `Timing Brief`, then ask one concise confirmation question. This gate applies in `run_mode: interactive` for both `lite` and `full` tiers. In `run_mode: autonomous` (or when the user explicitly requests speed / immediate output), do not ask: state the snapshot in one short paragraph, record unknowns in `open_questions`, and continue to Phase 4.

`Direction Snapshot` must include:
- scenario;
- audience;
- desired action or decision;
- success criteria;
- `brief_tier` and why;
- recommended narrative framework and why;
- downstream target, if any;
- key assumptions / open unknowns.

`Timing Brief` must include:
- total duration estimate;
- talk time vs Q&A reserve;
- slide count target;
- pacing model, such as fast pitch, steady report, workshop/training, demo-heavy, or executive brief;
- section-level time allocation;
- heavy slides likely to need extra time;
- compressed version if time is cut in half;
- overrun risks.

Ask a confirmation question like: “我会按这个方向和时长生成 brief。方向/时长对吗？要改听众、目标、叙事骨架、时长，还是直接继续？”

If the user corrects the direction or timing, revise the snapshot before continuing. If the user confirms or says “继续”, proceed to Phase 4. If speed is requested, state the snapshot in one short paragraph, record unknowns in `open_questions`, and continue without waiting.

### Phase 4 — Build the slide title chain

Create a slide-by-slide title chain with:
- slide number;
- narrative stage;
- conclusion-style title;
- slide job;
- evidence/assets;
- suggested visualization or layout intent;
- speaker-note focus.

Rewrite topic-only titles into claims. The title chain should be readable as a complete summary of the presentation.

### Phase 4.5 — Confirmation checkpoint (two-beat delivery)

By default, do not expand the full YAML contract yet. After direction and timing are confirmed, first send only the human-readable layer — the 摘要, Timing Brief, and Slide Title Chain table — and ask one concise question, e.g. “改哪几条标题或换骨架，还是直接展开完整 brief？”. The title chain is the artifact the user most needs to review and reject line by line, so let them steer it before you commit the rest.

Skip this checkpoint and go straight to the full output when `run_mode` is `autonomous`, when the user signals speed (“先出片”, “别问”, “直接给”, “just make it”), or when `brief_tier` is `lite` (a lite brief is already short enough to deliver in one beat).

### Phase 4.7 — Page-level content spec

After the direction/timing and title chain are accepted, read `references/content-spec-guide.md` before expanding the YAML.

For `full` briefs, every `slide_plan` item must include a complete `content_spec`:
- the page's single `primary_message`;
- concise on-slide copy blocks;
- a `visual_blueprint` for the main chart, infographic, screenshot, image, table, diagram, or no-visual page;
- `data_refs` that point to `evidence_plan[].id`;
- `asset_refs` that point to `asset_plan.catalog[].id`;
- narration timing and talking points;
- constraints, split conditions, and placeholder policy.

For `lite` briefs, add compact `content_spec` only when it prevents downstream ambiguity: key metrics, action asks, image/screenshot needs, or pages likely to overflow.

Downstream skills may translate `visual_blueprint` into their own layouts, presets, or components, but they must preserve `primary_message`, data values, caveats, required assets, and placeholder policy.

### Phase 5 — Data and evidence plan

Read `references/data-viz-guide.md` when the deck includes metrics, ROI, benchmarks, market sizing, timelines, comparisons, charts, or KPI cards.

For every key claim or metric, define:
- value and unit;
- source;
- `source_status`: `verified | user_reported | assumed | to_verify` (see core rule 16);
- comparison baseline;
- recommended chart;
- caveat/risk.

Assign each evidence item a stable `id` so `content_spec.visual_blueprint.primary_visual.data_refs` can reference it.

Mark missing sources or baselines as `待补来源` / `待补对比基准`; never fill with plausible-looking numbers. Any item whose `source_status` is `assumed` or `to_verify` must also be echoed in that page's `footnotes` and considered for the weakest-link self-check.

Build `asset_plan.catalog` with stable asset IDs for every logo, screenshot, photo, chart dataset, source document, video, or icon used by any page. Mark each item as `provided`, `extractable`, `to_fetch`, `to_generate`, `placeholder`, or `unavailable`; include permissions and fallback.

### Phase 6 — Speaker notes and Q&A plan

Read `references/speaker-notes-template.md` when the deck is for live presenting or when notes are requested or implied.

For each slide or high-risk section, specify:
- key talking points;
- timing;
- likely questions;
- answer direction;
- data source/definition if relevant.

Prepare explicit Q&A for high-risk pages: market size, financial forecast, competitor comparison, ROI, individual contribution, resource request, benchmark, limitation, security, compliance, or implementation risk.

### Phase 7 — Downstream handoff

When expanding the authoritative YAML, include the `Universal Handoff Contract` with these required top-level fields:
- `brief_tier`
- `run_mode`
- `output_language`
- `handoff_mode`
- `adapter_resolution`
- `deck_intent`
- `narrative`
- `runtime_plan`
- `slide_plan`
- `evidence_plan`
- `speaker_plan`
- `visual_intent`
- `asset_plan`
- `constraints`
- `must_keep`
- `must_avoid`
- `references_consulted`
- `open_questions`

Validate the assembled contract against `references/handoff-contract.schema.json` (field presence and enum values) before delivering.

If the user names a downstream skill, follow the runtime resolution protocol in `references/downstream-adapter-protocol.md`:
1. List the available skills in the current environment and fuzzy-match the user's named target.
2. Record the outcome in `adapter_resolution: {requested, resolved, status}` where status is `matched | unavailable | none`.
3. On `matched`: read the resolved skill's current `SKILL.md` completely, then only the references that define discovery questions, layout/style systems, output constraints, adapter vocabulary, or validation rules.
4. Translate the universal contract into the downstream skill's current terms so it can confirm instead of re-ask. Never invent its private fields.
5. On `unavailable` (named but not found) or `none` (no name given): keep `handoff_mode: universal_only`, do not guess a private contract, and list the downstream decisions still needed in `open_questions`: template system, supported layouts, animation model, editability, asset embedding, export format, and validation method.

Adapter examples are guidance only:
- For `frontend-slides-editable`, align with its discovery checklist, editable runtime needs, style intent, assets, mobile choice, slide count, and speaker-note handling.
- For `guizang-ppt-skill`, translate into its actual current style/theme/rhythm/layout vocabulary after reading it.
- For `huashu-design`, translate into its actual design spec, asset protocol, visual exploration process, and output constraints after reading it.

After the handoff is produced, decide whether to continue based on intent already expressed:
- No downstream skill named → stop and wait for the user's instruction.
- A downstream skill already named (e.g. the user said “交给 huashu-design”) → treat that as intent to continue; proceed to invoke that downstream skill with the brief, without asking a second confirmation. Exception: the user explicitly wants only the brief (“先不要做 HTML”, “只要 brief”).

### Phase 8 — Pre-delivery checklist

The canonical self-check lives in `references/presentation-checklist.md` (single source of truth). Read it before finalizing and run its scan, but do not report it as all green check marks. Instead name the **weakest 1–2 links** — the page, number, or claim where this deck would most likely fail in the room — and give a concrete fix for each. A self-check that passes everything is treated as no self-check at all. Any `assumed` / `to_verify` evidence (core rule 16) is a prime weakest-link candidate.

Before delivering, also confirm the contract validates against `references/handoff-contract.schema.json`: all required top-level fields present and all enum fields (`run_mode`, `source_status`, `spec_density`, `adapter_resolution.status`, `placeholder_policy`, …) within their allowed values.

## Output format

Prefer writing or returning a Markdown file named `presentation-strategy-brief.md`.

The contract YAML keys are always English (machine-stable). The human-readable layer (摘要 / Timing Brief / Slide Title Chain / weakest-link check) and all on-slide copy follow `output_language`. The Chinese section labels in the templates below are illustrative defaults for Chinese reporting — translate them when `output_language` differs.

Always order the human-readable layer first (摘要, then Timing Brief, then Slide Title Chain), then the authoritative YAML. Expand the YAML only after the Phase 4.5 confirmation checkpoint (or immediately when that checkpoint is skipped).

Keep the human-readable layer concise. Do not dump page-level `content_spec` before title-chain confirmation; put full page blueprints in the YAML handoff.

**Full tier** uses this exact structure:

````markdown
# Presentation Strategy Brief

## 摘要（人读）
- 一句话主张：
- 听众听完应记住：
- 听众听完应做：
- 推荐叙事骨架（及理由）：
- 推荐时长策略：
- 状态：信息完整 / 含 N 项待补

## Timing Brief（时长策略）
- 总时长预估：
- 正式讲述 / Q&A：
- 建议页数：
- 平均节奏：
- 重点页预计耗时：
- 可压缩版本：
- 超时风险：

## Slide Title Chain
| 页码 | 叙事阶段 | 结论式标题 | 本页作用 | 证据 / 素材 | 备注 |
| --- | --- | --- | --- | --- | --- |

## Universal Handoff Contract（权威）
```yaml
brief_tier: full
run_mode: interactive # or autonomous
output_language: zh # BCP-47-ish tag; human-readable layer follows this
handoff_mode: universal_only # or universal_plus_adapter
adapter_resolution:
  requested: none # downstream skill name the user asked for, or none
  resolved: none # the skill actually found in this environment, or none
  status: none # matched | unavailable | none
deck_intent:
  scenario: TBD
  audience: TBD
  desired_action: TBD
  success_criteria: TBD
narrative:
  framework: TBD
  rationale: TBD
  hook:
    type: TBD
    content: TBD
    first_30s: TBD
  stages: []
  closing:
    type: TBD
    content: TBD
runtime_plan:
  total_duration: TBD
  talk_time: TBD
  qa_time: TBD
  slide_count_target: TBD
  pacing: TBD
  section_allocation: []
  heavy_slides: []
  cut_if_short_on_time: []
  overrun_risks: []
slide_plan:
  - slide: 1
    stage: TBD
    spec_density: full # full | compact (see core rule 18)
    title: TBD # conclusion-style title
    job: TBD
    evidence: TBD
    asset_hint: TBD
    visual_hint: TBD
    speaker_note_focus: TBD
    content_spec:
      content_role: TBD
      primary_message: TBD
      on_slide_copy:
        headline: TBD
        subheadline: TBD
        body_blocks:
          - type: TBD
            text: TBD
        footnotes: []
      visual_blueprint:
        primary_visual:
          type: TBD
          purpose: TBD
          data_refs: []
          asset_refs: []
          annotation: TBD
        layout_intent:
          composition: TBD
          hierarchy: TBD
          density: TBD
      data_requirements:
        metrics: []
        missing_sources: []
      asset_requirements:
        required: []
        optional: []
        fallback: TBD
      narration:
        talk_time: TBD
        key_talking_points: []
      constraints:
        must_include: []
        must_avoid: []
        split_if: []
        placeholder_policy: honest_placeholder
evidence_plan:
  - id: ev-tbd
    claim_or_metric: TBD
    source: 待补来源
    source_status: to_verify # verified | user_reported | assumed | to_verify
    comparison_baseline: 待补对比基准
    recommended_chart: TBD
    caveat: TBD
speaker_plan:
  qa_risks: []
  timing: TBD # derive from runtime_plan; add per-slide notes where needed
visual_intent:
  tone: TBD
  density: TBD
  rhythm: TBD
  readability: TBD
asset_plan:
  catalog:
    - id: asset-tbd
      type: TBD
      status: TBD
      source: TBD
      rights_or_permission: TBD
      used_on: []
      fallback: TBD
  have: []
  todo: []
constraints:
  language: TBD
  duration: TBD
  slide_count: TBD
  editability: TBD
  portability: TBD
  brand_assets: TBD
must_keep: []
must_avoid: []
references_consulted: [] # which references/*.md were actually read
open_questions: []
```

## Adapter-specific Appendix（仅在指定且可读取下游 skill 时追加）
```yaml
# Use the downstream skill's current vocabulary. Do not invent private fields.
```

## 交付前自检（最弱环）
- 最可能翻车处 1：<哪页/哪个数字/哪个断言> → 修复：
- 最可能翻车处 2（如有）：→ 修复：
- 其余 12 问扫描通过项：简列，不逐条打勾
````

**Lite tier** drops the heavy contract. Use this shorter structure:

````markdown
# Presentation Strategy Brief（lite）

## 摘要（人读）
- 一句话主张：
- 听众听完应记住：
- 听众听完应做：
- 推荐叙事骨架（及理由）：
- 推荐时长策略：
- 状态：信息完整 / 含 N 项待补

## Timing Brief（时长策略）
- 总时长预估：
- 正式讲述 / Q&A：
- 建议页数：
- 可压缩版本：
- 超时风险：

## Slide Title Chain
| 页码 | 叙事阶段 | 结论式标题 | 本页作用 | 备注 |
| --- | --- | --- | --- | --- |

## Handoff Contract（精简）
```yaml
brief_tier: lite
run_mode: interactive # or autonomous
output_language: zh
handoff_mode: universal_only # or universal_plus_adapter
adapter_resolution:
  requested: none
  resolved: none
  status: none # matched | unavailable | none
deck_intent:
  scenario: TBD
  audience: TBD
  desired_action: TBD
constraints:
  language: TBD
  duration: TBD
  slide_count: TBD
runtime_plan:
  total_duration: TBD
  talk_time: TBD
  qa_time: TBD
  slide_count_target: TBD
  cut_if_short_on_time: []
slide_plan:
  - slide: 1
    title: TBD
    job: TBD
    content_spec:
      primary_message: TBD
      on_slide_copy:
        headline: TBD
        body_blocks: []
      primary_visual:
        type: none
        data_refs: []
        asset_refs: []
      split_if: []
references_consulted: []
open_questions: []
```

## 交付前自检（最弱环）
- 最可能翻车处：<…> → 修复：
````

Omit `evidence_plan` / `speaker_plan` / `visual_intent` skeletons in lite. If one matters (e.g. a single high-risk number), add it as one inline line under the relevant slide, not as a full section.

## Quality bar

Judge against the chosen `brief_tier`. A lite brief is not deficient for omitting evidence/speaker sections.

A good **full** brief:
- states scenario, audience, desired action, and success criteria;
- recommends and explains a narrative framework;
- includes a realistic timing brief with talk/Q&A split, page count, pacing, heavy pages, compression path, and overrun risks;
- provides a complete conclusion-style slide title chain;
- assigns one job to every slide;
- includes complete `content_spec` for every slide so downstream skills do not need to invent copy, charts, image slots, or content modules;
- gives data sources, units, comparison baselines, chart recommendations, and caveats;
- tags every evidence item with `source_status`, and never dresses a `user_reported`/`assumed` number as `verified`;
- gives stable evidence IDs and asset catalog IDs, and uses them from each page's `content_spec`;
- marks each slide's `spec_density`, keeping the contract handoff-sized on long decks;
- records `adapter_resolution` honestly and degrades to `universal_only` when a named downstream cannot be resolved;
- validates against `references/handoff-contract.schema.json` and lists `references_consulted`;
- includes a hook, close, speaker notes, timing, and Q&A risks;
- contains the universal contract even when no downstream skill is known;
- marks unknowns as `待补` / `TBD` instead of fabricating;
- names its weakest 1–2 links instead of self-grading all-pass;
- can be handed directly to any competent slide-generation skill.

A good **lite** brief:
- states scenario, audience, and desired action;
- includes a compact timing brief with total duration, talk/Q&A split, slide count, and compression path;
- provides a conclusion-style title chain with one job per slide;
- uses compact `content_spec` only for key metrics, action asks, image/screenshot needs, or likely-overflow pages;
- captures only the constraints a generator needs (language, duration, slide count, downstream);
- marks unknowns as `待补` / `TBD`;
- stays short enough to deliver in one beat.
