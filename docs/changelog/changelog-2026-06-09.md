# 2026-06-09 — STORYBOARD domain: 화면설계서/기능명세 via bridge to storyboard-spec

## What changed

Added a 10th PM domain, **STORYBOARD**, that turns a validated direction (discovery/research/PRD)
into a storyboard-style 화면설계서 (screen design document) whose per-element table doubles as the
기능명세 (functional spec).

New:
- `reference/storyboard.md` — the domain framework (upstream contract, Mode A/B, element-extraction
  checklist, storyboard structure, production decision block, critic completeness anchors).
- `templates/storyboard-page.html` — self-contained one-screen page (inline CSS/JS, zero external
  deps). Left = wireframe/replica with numbered callouts; right = the 5-column element table.
- `templates/storyboard-board.html` — self-contained thumbnail/index board using live `<iframe>`
  thumbnails (no screenshot tooling needed).

Edited (surgical):
- `SKILL.md` — STORYBOARD row in the intent table, reference-map row, templates note, and the
  frontmatter `description` (added screen-design / 화면설계서 triggers so the route actually fires).
- `docs/DESIGN.md` — layout tree + a section on the bridge/standalone integration + credit.
- `README.md`, `README.ko.md` — domain table row, layout lines, credit; "9 → 10" route count.
- `docs/index.html` — a STORYBOARD mode-card (color `--blue`) and the "nine/9 → ten/10" count
  copy across hero/marquee/metric/headings/CTA (EN+KO). Left "68 PM skills across 9 plugins"
  (an upstream fact) and the 68→9 compression claim intact, noting screen-design is additive.

## Decisions and why

- **Bridge + delegate, standalone by default (not absorb, not hard-dependency).** The user
  requires superpm to work with `storyboard-spec` absent. So superpm renders the full 화면설계서
  from bundled self-contained HTML, and only *delegates the heavy rendering* (Figma REST
  auto-extraction, headless thumbnails, themeable CSS) to `storyboard-spec` when it is installed
  (detected at `~/.claude/skills/storyboard-spec/SKILL.md`). This matches DESIGN.md's existing
  "no runtime dependency" principle. Absorbing storyboard-spec's ~500-line playbook + scripts was
  rejected as duplication that would drift out of sync.

- **The right-pane element table IS the 기능명세 (one artifact, not two).** Per superpm's
  "smallest useful artifact" principle: each element row carries 동작(event) / 데이터(data) /
  예외(exception) / 상태(state), which is exactly a per-screen functional spec. No separate
  functional-spec document.

- **Standalone output is a self-contained single HTML, not markdown.** 화면설계서 is inherently a
  visual document; a markdown-only fallback would lose the side-by-side storyboard. The bundled
  templates use the same `{{...}}` / `sb-mark` / `sb-cue` / `sb-notes` contract as storyboard-spec,
  so a doc started standalone upgrades cleanly if that skill is added later.

- **Live `<iframe>` thumbnails for the board.** storyboard-spec's board relies on `shoot.sh`
  (headless-Chrome PNGs). To stay dependency-free, the bundled board scales each page in an
  `<iframe>` instead — real thumbnails, zero build step. (A commented `<img src="thumbs/*.png">`
  alternative is left in for when storyboard-spec/shoot.sh is present.)

- **Domain name STORYBOARD, placed after EXECUTE.** Lifecycle order: discovery/research → PRD →
  screen design → build. User chose the name; "SCREENS"/"DESIGN-SPEC" were the alternatives.

## Verification

- Rendered `templates/storyboard-page.html` and `templates/storyboard-board.html` in headless
  Chrome from a temp dir (no network): page shows the login wireframe with 4 numbered callouts
  mapped 1:1 to the 4 tagged element rows; board shows two cards with live iframe thumbnails of the
  actual pages. Both fully self-contained.
- `grep` confirmed zero external `http(s)://`, `<link rel=stylesheet>`, or `<script src>` in either
  template — only local relative links/iframes.
- Critic self-review of `reference/storyboard.md` against `reference/critic.md`'s four checks:
  completeness (all framework sections + anchors present), evidence (every referenced path now
  exists), decision-fit (drives the 화면설계서/기능명세 deliverable), assumption-surface (the
  standalone-vs-delegate logic is explicit). No blockers.

---

# 2026-06-09 — DISCOVER: idea-proposal house style (decision-grade brainstorm output)

## What changed

`reference/discover.md` `brainstorm-ideas` — added an **Idea-proposal format** as the default
output when the user wants a recommendation (not a 10-20 divergent list). The existing lenses and
divergent output are preserved (relabeled "Divergent output").

The new format encodes a reproducible house style:
- Batch header naming the round's axis theme; 3 bets each on a *distinct customer/model axis*;
  "another / different one" jumps to a genuinely new axis, not a re-skin of the last round.
- Per-idea skeleton: `X. concept (customer+model tag) <- 추천` + 누가→무엇 / 무료 미끼 /
  수익화 / 차별화(복제난이도) / 왜 지금(winner) · 주의(runners-up).
- Comparison table (revenue ceiling | fit | marketing-CAC | copy-difficulty | validation speed),
  one decisive pick with a punchy one-line why, timeboxed cheapest validation (experiment /
  numeric threshold / decision rule), compact critic, next-move offer.
- Principle baked in: *lucrative lives in distribution and moat, not the product*; never assert a
  market size / revenue figure as fact.

## Decisions and why

- **Additive, not replacing.** Kept the 10-20 divergent menu for pure ideation; added the
  convergent decision-grade format as the default for "what should we bet on" requests. Surgical
  edit to one section.
- **Codified from a user-approved gold sample.** The format mirrors a P/Q/R "model-shift" idea set
  the user explicitly flagged as the desired feel (punchy titles, per-idea 왜지금/주의 asymmetry,
  memorable economic framing, timeboxed validation).
- **Critic kept but compact.** superpm's independent-critic gate stays; when per-idea 주의 already
  carries the two-sided risks, the trailing Critic stays short (market numbers / competitor claims
  must still be labeled assumptions).

## Verification

- Edit applied to `reference/discover.md`; `brainstorm-experiments` and other sections untouched.
- Format derived from an in-session sample the user confirmed; no runtime/scripted component to test.
