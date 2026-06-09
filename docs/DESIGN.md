# superpm - design

One PM request in, a decision-ready artifact out - the smallest useful artifact,
checked by an independent critic against the framework and the real decision.

## Why this exists

`phuryn/pm-skills` is a marketplace of 68 PM skills across 9 plugins. Every skill is a
separate file you load by name. `superpm` folds that catalog into **one skill**: the model
captures intent from the request, the workflow **diverges by PM domain** into the right
framework, and an independent critic verifies the result before it ships.

The verification discipline is adapted 1:1 from `supergoal` (baseline-first delivery).

## The supergoal -> superpm mapping

| supergoal (code) | superpm (PM) |
|---|---|
| Verify against ground truth (re-run REAL tests) | Verify against **framework completeness + the real decision** (independent critic/red-team) |
| Smallest correct change | **Smallest useful artifact** - answer the actual decision, no filler frameworks |
| Surface hidden requirements as FAILING tests | Surface **hidden assumptions as risks** the critic flags |
| Ambiguity-gated <=5 question interview | Same intent-capture interview gate |
| Modes: greenfield / debug / legacy / learn / ... | **PM domains**: discover / strategy / execute / research / analytics / gtm / growth / toolkit / ai-ship |
| Never optimize to a self-graded proxy | Never let a framework template stand in for the user's real decision context |

## Core decision: one workflow, domain-routed divergence

The "diverging workflow" is **not** nine different loops. It is one loop whose divergence is
*which reference (domain framework) gets loaded*. Intent capture picks the domain and the
artifact; the loop is universal:

```
Capture -> Frame -> Draft -> Critic -> Deliver
```

1. **Capture** - classify the PM ask into a domain + a target artifact. If genuinely
   ambiguous, run `reference/intent.md` (<=5 questions); resolve doc/code-answerable
   questions by reading, not asking.
2. **Frame** - state in one line the real decision this artifact must serve and its
   completion bar.
3. **Draft** - apply the domain framework from `reference/<domain>.md`. Smallest useful
   artifact; no filler frameworks bolted on.
4. **Critic (independent)** - run `reference/critic.md`: red-team for missing sections,
   unsupported claims, and unvalidated assumptions; emit them as risks.
5. **Deliver** - fold the surfaced risks back in, then stop. Report what was checked.
   Any irreversible/outward step (publish, send, post to a tracker) needs explicit consent.

## Layout

```
SKILL.md          thin spine: principles, intent-capture table, the loop, reference map
reference/
  intent.md       intent classification + <=5 question interview gate
  critic.md       independent critic / red-team verification gate
  discover.md     pm-product-discovery frameworks
  strategy.md     pm-product-strategy frameworks
  execute.md      pm-execution frameworks
  storyboard.md   화면설계서/기능명세 storyboard - bundled-standalone, delegates to storyboard-spec if installed
  research.md     pm-market-research frameworks
  analytics.md    pm-data-analytics frameworks
  gtm.md          pm-go-to-market frameworks
  growth.md       pm-marketing-growth frameworks
  toolkit.md      pm-toolkit utilities
  ai-ship.md      pm-ai-shipping frameworks (ties back to supergoal's verification ethos)
templates/        high-value artifact templates (PRD, strategy canvas, OST, battlecard, ...)
  storyboard-page.html   self-contained one-screen 화면설계서 page (inline CSS, no deps)
  storyboard-board.html  self-contained thumbnail/index board (live iframe thumbs)
docs/DESIGN.md    this file
```

## Self-containment

The 68 upstream skills are compressed into the 9 domain references at a usable depth - no
runtime dependency on `phuryn/pm-skills`. References name the canonical framework so a reader
can go deeper upstream if wanted, but `superpm` runs standalone.

## STORYBOARD domain: bridge to storyboard-spec, standalone by default

The STORYBOARD domain produces 화면설계서/기능명세 (screen design documents): per the
self-containment principle above, superpm renders the full document with **zero external
dependency**, using two bundled self-contained HTML templates (`templates/storyboard-page.html`,
`templates/storyboard-board.html`) - inline CSS/JS only, opens straight in a browser.

`cskwork/storyboard-spec` is a separate, richer skill for the same artifact (Figma REST
auto-extraction, headless-Chrome thumbnails, themeable CSS). It is treated as an **optional
accelerator, never a hard dependency**: `reference/storyboard.md` detects it
(`~/.claude/skills/storyboard-spec/SKILL.md`) and, only if present, delegates the heavy rendering
to it. The bundled templates use the same `{{...}}` / `sb-mark` / `sb-cue` / `sb-notes` contract
as storyboard-spec, so a document started standalone upgrades cleanly if that skill is later
installed.

The artifact also folds 기능명세 into the same deliverable: the right-pane per-element table
(action / data / exception / state) *is* the functional spec - one document, not two. The critic
gate extends to screens via `reference/storyboard.md`'s completeness anchors (no dead-end screens,
1:1 callout-to-row, sourced data contracts, non-happy states covered).

## Credit

- PM framework catalog: `phuryn/pm-skills` (MIT), curated by Pawel Huryn.
- Workflow + verification discipline: `cskwork/supergoal-skill` (MIT).
- Screen-design storyboard method (optional accelerator + bundled-template contract):
  `cskwork/storyboard-spec` (MIT).
