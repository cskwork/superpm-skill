---
name: superpm
description: Single-skill PM operating system. Capture intent from the request, diverge by PM domain into the right framework (discovery, strategy, execution, research, analytics, GTM, growth, toolkit, AI-shipping), produce the smallest useful artifact, and verify it with an independent critic before delivery. Use for "/superpm", "superpm", "write a PRD", "product strategy", "OKRs", "roadmap", "opportunity solution tree", "competitor analysis", "market sizing", "pricing", "personas", "cohort / A/B analysis", "GTM / launch plan", "positioning", "review my resume", or any product-management artifact.
---

# /superpm - one PM request, a verified artifact

One PM ask -> capture intent -> diverge by domain -> the smallest useful artifact -> an
independent critic checks it against the framework and the real decision -> stop.

The catalog of 68 PM frameworks lives in `reference/`. This file is the spine: it classifies
the ask, names the loop, and points at the right reference. For a one-paragraph note you could
write directly, skip the skill and write it.

## Principles

- **Serve the real decision.** Every artifact answers a decision someone will act on. Name that
  decision before drafting. A framework filled in for its own sake is waste.
- **Smallest useful artifact.** Apply only the frameworks the decision needs. Do not bolt on a
  SWOT, a persona, and a roadmap when the ask was one pricing call.
- **Ground claims in evidence.** Numbers, quotes, and segments come from the user's data, docs,
  or named assumptions - never invented. Mark every assumption as an assumption.
- **Surface hidden assumptions first.** The one place a process beats a plain draft: an
  independent critic names the unstated assumptions and missing pieces as risks.
- **Ask only when genuinely ambiguous.** Resolve anything answerable from the repo, attached
  docs, or data by reading it. Interview only load-bearing, user-only choices (`reference/intent.md`).
- **Hard stops.** Anything irreversible or outward-facing - publishing, sending, posting to a
  tracker, sharing externally - needs explicit consent. Never present an assumption as a fact.

## Intent capture - signal to domain

Read the request and route to one domain (the artifact named usually decides it). When the ask
spans domains, pick the primary deliverable and pull supporting frameworks from the others.

| Signal in the request | Domain | Reference |
|---|---|---|
| brainstorm ideas / risky assumptions / opportunity tree / prioritize features / customer interview / metrics | **DISCOVER** | `reference/discover.md` |
| product strategy / vision / value proposition / lean or business model / monetization / pricing / SWOT / PESTLE / Porter / Ansoff | **STRATEGY** | `reference/strategy.md` |
| PRD / OKRs / roadmap / sprint plan / retro / pre-mortem / user or job stories / stakeholder map / prioritization framework / red-team a plan | **EXECUTE** | `reference/execute.md` |
| personas / segments / customer journey / market sizing (TAM/SAM/SOM) / competitor analysis / sentiment | **RESEARCH** | `reference/research.md` |
| SQL from a question / cohort analysis / A/B test read-out | **ANALYTICS** | `reference/analytics.md` |
| go-to-market / beachhead / ICP / growth loops / GTM motion / battlecard | **GTM** | `reference/gtm.md` |
| marketing ideas / positioning / value-prop statements / product name / North Star metric | **GROWTH** | `reference/growth.md` |
| review or tailor a resume / draft an NDA or privacy policy / proofread | **TOOLKIT** | `reference/toolkit.md` |
| document an AI-built app / shipping artifacts / intended-vs-implemented gap | **AI-SHIP** | `reference/ai-ship.md` |

The domain decides *which frameworks load*. The loop below is the same for all of them.

## The loop - Capture, Frame, Draft, Critic, Deliver

1. **Capture.** Classify domain + target artifact from the request. If genuinely
   underspecified, run the `reference/intent.md` gate (<=5 questions, one round, recommend an
   answer for each). Resolve doc/data-answerable questions by reading, not asking.

2. **Frame.** Write one line: *the real decision this artifact serves* and *its completion bar*
   (what "done and trustworthy" looks like for this framework). This is the bar the critic
   checks against.

3. **Draft.** Load `reference/<domain>.md` and apply the named framework. Use the user's real
   inputs; mark gaps as explicit assumptions. Smallest useful artifact - no filler frameworks.

4. **Critic (independent).** Run `reference/critic.md` as a fresh reader who did not write the
   draft. Red-team it: missing framework sections, unsupported claims, unvalidated assumptions,
   decisions the artifact dodges. Emit each as a risk. Do not self-congratulate a draft to green.

5. **Deliver.** Fold the surfaced risks back into the artifact (or list the ones the user must
   resolve), then stop. Report what was checked and against what. Outward/irreversible steps
   wait for explicit consent.

## Reference map

| Read | When |
|---|---|
| `reference/intent.md` | Capture: ambiguity-gated <=5 question interview before drafting |
| `reference/critic.md` | Critic: independent red-team verification gate (every domain) |
| `reference/discover.md` | DISCOVER: ideation, assumptions, OST, prioritization, interviews, metrics |
| `reference/strategy.md` | STRATEGY: strategy canvas, vision, value prop, lean/business model, pricing, analysis frameworks |
| `reference/execute.md` | EXECUTE: PRD, OKRs, roadmap, sprint, retro, pre-mortem, stories, stakeholder map, prioritization |
| `reference/research.md` | RESEARCH: personas, segments, journey map, market sizing, competitor, sentiment |
| `reference/analytics.md` | ANALYTICS: NL->SQL, cohort, A/B test |
| `reference/gtm.md` | GTM: strategy, beachhead, ICP, growth loops, motions, battlecard |
| `reference/growth.md` | GROWTH: marketing ideas, positioning, value-prop statements, naming, North Star |
| `reference/toolkit.md` | TOOLKIT: resume, NDA, privacy policy, proofread |
| `reference/ai-ship.md` | AI-SHIP: shipping artifacts, intended-vs-implemented |
| `templates/` | Reusable artifact scaffolds (PRD, strategy canvas, OST, battlecard, ...) |

## Output language

Write the artifact in the user's language. Keep framework names, metric names, and
machine-checked anchors (SQL, identifiers, file paths) in their canonical form.
