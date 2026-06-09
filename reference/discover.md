# DISCOVER - product discovery

Frameworks for finding what to build and de-risking it before commitment. Branch hard on
**new product** (no users/data yet) vs **existing product** (real users, telemetry, requests).

## brainstorm-ideas

Generate solution ideas from multiple lenses, then converge.

- **Lenses:** jobs-to-be-done, current pain points, competitor gaps, adjacent workflows, tech
  enablers, business-model shifts. Existing product: also mine support tickets, churn reasons,
  feature requests. New product: also mine analogous markets and first-principles needs.
- **Output:** 10-20 ideas, each as `<who> can now <do what> so that <outcome>`. Cluster by
  theme; flag the 3 worth testing first and why.

## brainstorm-experiments

Design the cheapest test that could disconfirm an assumption.

- **Existing:** A/B test, fake door, feature flag rollout, concierge, painted door, instrumented
  prototype. Define the metric and the decision threshold up front.
- **New (pretotyping, Savoia):** pinocchio, mechanical turk, provincial, fake-door landing page,
  YouTube/one-night-stand. Measure with skin-in-the-game data (signups, pre-orders), not opinions.
- **Output per experiment:** assumption tested, method, success metric + threshold, cost/time,
  what each outcome decides.

## identify-assumptions

List what must be true for the idea to succeed - the things that, if false, kill it.

- **Existing product - four risks (Cagan):** Value (will they want it?), Usability (can they use
  it?), Feasibility (can we build it?), Viability (does it work for the business?).
- **New product - eight risks:** value, demand, usability, feasibility, viability, channel,
  market-timing, legal/regulatory.
- **Output:** assumptions grouped by category, each phrased as a falsifiable statement.

## prioritize-assumptions

Plot assumptions on **Impact x Risk** (Torres "leap of faith"): high-impact + high-uncertainty
= test first. For each top assumption, suggest the cheapest experiment (link to
brainstorm-experiments) and the decision its result drives.

## prioritize-features

Rank a backlog by **impact, effort, risk, strategic alignment**. Use a named framework from
`execute.md` (RICE/ICE) for the score; never rank on gut alone. Output a ranked table with the
score components visible and the cut line called out.

## analyze-feature-requests

Categorize raw requests by theme, underlying job, and fit with strategy. Output: themes ranked
by frequency x segment-value, the job behind each, and a keep/park/decline call per theme with
reasoning - not a promise to build.

## opportunity-solution-tree (Teresa Torres)

Structure discovery as a tree:

```
Desired Outcome (one measurable business/product outcome)
└── Opportunities (customer needs, pains, desires - from research, not solutions)
    └── Solutions (ideas that address the opportunity)
        └── Experiments (tests that de-risk the solution)
```

Rules: opportunities are needs phrased in the customer's words, never solutions. One outcome per
tree. Compare solutions *within* an opportunity, not across. Output the tree + the opportunity
you would pursue first and why.

## interview-script (JTBD)

Customer interview script anchored in jobs-to-be-done and the moment of struggle.

- **Structure:** warm-up -> last time you faced <problem> (story, not hypotheticals) -> what did
  you do / try / hire -> what was hard -> what would "great" look like. Ask about the past, not
  the future. No leading questions, no pitching.
- **Output:** 8-12 open questions + probes, sequenced.

## summarize-interview

Transcript -> structured signal: the job, the struggling moment, current solutions + workarounds,
desired outcomes, surprises, verbatim quotes, and 3-5 action items. Separate observation
(what they said) from interpretation (what you infer).

## metrics-dashboard

Define the measurement frame: **North Star metric** (the one value-capture metric), 3-5 **input
metrics** that move it, guardrail metrics, and alert thresholds. Tie each input metric to a lever
the team controls. Output: the metric tree + why the North Star captures delivered value.

## Critic completeness anchors

OST has exactly one outcome and no solutions masquerading as opportunities; assumptions are
falsifiable and risk-categorized; experiments name a threshold and a decision; metric trees link
inputs to the North Star.
