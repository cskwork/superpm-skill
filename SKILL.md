---
name: superpm
description: PM operating system - route a PM ask to its domain framework (discovery, strategy, execution, screen design, research, analytics, GTM, growth, toolkit, AI-shipping), draft the smallest useful artifact, verify with an independent critic. Use for "/superpm", "superpm", "write a PRD", "product strategy", "OKRs", "roadmap", "opportunity solution tree", "user stories", "pre-mortem", "retro", "release notes", "interview script", "화면설계서 / 기능명세", "competitor analysis", "market sizing", "pricing", "personas", "cohort / A/B analysis", "GTM / launch plan", "ICP", "battlecard", "positioning", "North Star metric", "review my resume", "what are people saying", "market signal / voice of customer / trends", or any product-management artifact.
---

# /superpm - one PM request, a verified artifact

One PM ask -> capture intent -> diverge by domain -> the smallest useful artifact -> an
independent critic checks it against the framework and the real decision -> stop.

68 PM frameworks live in `reference/`; this file routes the ask and names the loop. For a
one-paragraph note you could write directly, skip the skill.

## Principles

- **Serve the real decision.** Name the decision the artifact drives before drafting; a
  framework filled in for its own sake is waste.
- **Smallest useful artifact.** Only the frameworks the decision needs - no bolted-on
  SWOT/persona/roadmap when the ask was one pricing call.
- **Ground claims in evidence.** Numbers, quotes, segments come from the user's data, docs, or
  named assumptions - never invented. Market/customer claims: pull real signal via
  `reference/signal.md` (read-only, keyless) before asserting.
- **Surface hidden assumptions.** The critic names unstated assumptions and missing pieces as
  risks - never present an assumption as fact.
- **Ask only when genuinely ambiguous.** Read the repo/docs/data first; interview only
  load-bearing, user-only choices (`reference/intent.md`).
- **Hard stops.** Irreversible or outward-facing actions (publish, send, post, share
  externally) need explicit consent.

## Intent capture - signal to domain

Read the request and route to one domain (the artifact named usually decides it). When the ask
spans domains, pick the primary deliverable and pull supporting frameworks from the others.

| Signal in the request | Domain | Reference |
|---|---|---|
| brainstorm ideas / risky assumptions / opportunity tree / prioritize features / customer interview / metrics | **DISCOVER** | `reference/discover.md` |
| product strategy / vision / value proposition / lean or business model / monetization / pricing / SWOT / PESTLE / Porter / Ansoff | **STRATEGY** | `reference/strategy.md` |
| PRD / OKRs / roadmap / sprint plan / retro / pre-mortem / user or job stories / stakeholder map / prioritization framework / red-team a plan | **EXECUTE** | `reference/execute.md` |
| 화면설계서 / 기능명세 / 스토리보드 / screen design doc / screen spec / wireframe / UI spec | **STORYBOARD** | `reference/storyboard.md` |
| personas / segments / customer journey / market sizing (TAM/SAM/SOM) / competitor analysis / sentiment | **RESEARCH** | `reference/research.md` |
| SQL from a question / cohort analysis / A/B test read-out | **ANALYTICS** | `reference/analytics.md` |
| go-to-market / beachhead / ICP / growth loops / GTM motion / battlecard | **GTM** | `reference/gtm.md` |
| marketing ideas / positioning / value-prop statements / product name / North Star metric | **GROWTH** | `reference/growth.md` |
| review or tailor a resume / draft an NDA or privacy policy / proofread | **TOOLKIT** | `reference/toolkit.md` |
| document an AI-built app / shipping artifacts / intended-vs-implemented gap | **AI-SHIP** | `reference/ai-ship.md` |

The domain decides which reference loads; the loop is the same for all. Cross-cutting: asks
about *what the market/customers want* (demand, trends, voice of customer) ground the artifact
in `reference/signal.md` first.

## The loop - Capture, Frame, Draft, Critic, Deliver

1. **Capture.** Classify and record one line - `Domain: <X> | Artifact: <Y> | Decision it
   serves: <Z>` - even when nothing is ambiguous. If genuinely underspecified, run the
   `reference/intent.md` gate (<=5 questions, one batched round, a recommended answer per
   question). Resolve doc/data-answerable questions by reading, not asking.

2. **Frame.** Extend that line into the artifact's `## Intent` block: classification, the real
   decision, and the completion bar (what "done and trustworthy" looks like for this
   framework). This block is the contract the critic checks against.

3. **Draft.** Load `reference/<domain>.md` and apply the named framework. Use the user's real
   inputs; mark gaps as explicit assumptions. Smallest useful artifact - no filler frameworks.

4. **Critic (independent).** Run `reference/critic.md`. Independence is mechanical: if the
   harness supports subagents, hand a fresh one only the `## Intent` block + the draft;
   otherwise switch stance and read cold. Red-team: missing framework sections, unsupported
   claims, unvalidated assumptions, dodged decisions - each emitted as a risk. Do not
   self-congratulate a draft to green.

5. **Deliver.** Fold blockers and gaps back in; leave user-owned risks in a `## Critic` block.
   Response shape: artifact -> remaining risks -> one line on what was checked against what ->
   the one natural next artifact in the chain (DISCOVER -> STRATEGY -> EXECUTE -> STORYBOARD ->
   GTM/GROWTH; ANALYTICS measures any) - offer it, don't start it. Inline by default; write
   files when multi-page or multi-file (storyboard: always files) and report paths.
   Outward/irreversible steps wait for explicit consent.

## Follow-up turns

The loop is per-artifact, not per-message. On iteration:

- Substantive change (new claim, section, or decision) -> re-Draft, re-run the critic on the
  delta only.
- Tone / format / length-only edits -> no critic re-run.
- New artifact or new domain -> new loop from Capture. "Another idea / different one" in
  DISCOVER follows the idea-proposal batch rule (`reference/discover.md`).
- Keep the loaded domain reference; do not re-read it each turn.

## Reference map

| Read | When |
|---|---|
| `reference/intent.md` | Capture: ambiguity-gated <=5 question interview before drafting |
| `reference/critic.md` | Critic: independent red-team verification gate (every domain) |
| `reference/signal.md` | Signal: live market & customer evidence (voice of customer), read-only + keyless; feeds RESEARCH/DISCOVER/GTM, delegates to the `last30days` skill if present |
| `reference/discover.md` | DISCOVER: ideation, assumptions, OST, prioritization, interviews, metrics |
| `reference/strategy.md` | STRATEGY: strategy canvas, vision, value prop, lean/business model, pricing, analysis frameworks |
| `reference/execute.md` | EXECUTE: PRD, OKRs, roadmap, sprint, retro, pre-mortem, stories, stakeholder map, prioritization |
| `reference/storyboard.md` | STORYBOARD: 화면설계서/기능명세 - derive screens, wireframe (Mode B) or replica (Mode A), per-element spec; standalone via bundled HTML, delegates to the `storyboard-spec` skill if present |
| `reference/research.md` | RESEARCH: personas, segments, journey map, market sizing, competitor, sentiment |
| `reference/analytics.md` | ANALYTICS: NL->SQL, cohort, A/B test |
| `reference/gtm.md` | GTM: strategy, beachhead, ICP, growth loops, motions, battlecard |
| `reference/growth.md` | GROWTH: marketing ideas, positioning, value-prop statements, naming, North Star |
| `reference/toolkit.md` | TOOLKIT: resume, NDA, privacy policy, proofread |
| `reference/ai-ship.md` | AI-SHIP: shipping artifacts, intended-vs-implemented |
| `templates/` | Reusable artifact scaffolds (PRD, strategy canvas, OST, battlecard, storyboard page/board, ...) |

## Output language

Write the artifact in the user's language. Keep framework names, metric names, and
machine-checked anchors (SQL, identifiers, file paths) in their canonical form.
