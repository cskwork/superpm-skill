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
  research.md     pm-market-research frameworks
  analytics.md    pm-data-analytics frameworks
  gtm.md          pm-go-to-market frameworks
  growth.md       pm-marketing-growth frameworks
  toolkit.md      pm-toolkit utilities
  ai-ship.md      pm-ai-shipping frameworks (ties back to supergoal's verification ethos)
templates/        high-value artifact templates (PRD, strategy canvas, OST, battlecard, ...)
docs/DESIGN.md    this file
```

## Self-containment

The 68 upstream skills are compressed into the 9 domain references at a usable depth - no
runtime dependency on `phuryn/pm-skills`. References name the canonical framework so a reader
can go deeper upstream if wanted, but `superpm` runs standalone.

## Credit

- PM framework catalog: `phuryn/pm-skills` (MIT), curated by Pawel Huryn.
- Workflow + verification discipline: `cskwork/supergoal-skill` (MIT).
