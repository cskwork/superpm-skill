# STORYBOARD - screen design documents (화면설계서)

Frameworks for turning a validated direction into a **storyboard-style screen design document**
(화면설계서): each screen drawn or replicated with numbered callouts on the left, and a per-element
table on the right. That right-hand table (action / data / exception / state) **is** the functional
spec (기능명세) - one artifact serves planners and API/frontend devs at once. Runs after
discovery/research (and usually a PRD) has settled *what* to build; this settles *how each screen
behaves*.

The bias: one screen (or one state) per page, every interactive element accounted for, no orphan
callouts, and every data/exception named or marked an assumption.

## Upstream contract - where the screen list comes from

Do not invent screens. Derive them from what the prior loop produced:

- **Customer journey map** (`research.md`) -> one screen per stage / moment of truth.
- **PRD section 6 UX/flows + user stories** (`execute.md`) -> one screen per step in the key flow;
  one extra page per non-happy state (empty / error / loading / permission).
- **OST solutions** (`discover.md`) -> the screens the chosen solution requires.

Output of this step: a flat screen list, each row `SCREEN_ID | title | state | prev -> next`. A
screen with no entry/exit is incomplete - every screen is reachable and leads somewhere.

## Mode - B (기획) vs A (문서화)

Branch on whether the UI exists yet:

- **Mode B (기획 / plan-first)** - no UI yet. Draw a low-fi **wireframe** from the requirements
  (boxes, labels, inputs), then number and annotate it. The design-up-front path; most pre-build
  work is here.
- **Mode A (문서화 / document)** - a built screen or Figma frame exists. Replicate it (paste the
  real markup, or embed a screenshot / Figma export) and annotate that. The left side matches the
  real screen; the right table describes it.

State the mode per screen.

## Element-extraction checklist - this IS the 기능명세

For each screen, walk the UI and list every element a user touches or that carries data. Each one
becomes a callout row:

1. **No** - callout number; matches the marker on the left 1:1.
2. **구역 / area** - which region of the screen (header, form, list, footer...).
3. **요소 / ID** - the element name + its DOM id or selector (so devs can find it).
4. **설명 / behavior**, tagged by kind:
   - **동작 (event)** - what firing it does (click -> validate -> POST /sessions).
   - **데이터 (data)** - the data contract in/out (field, type, source API, validation rule).
   - **예외 (exception)** - failure / empty / permission behavior and the message shown.
   - **상태 (state)** - enabled / disabled / loading / selected variants, if any.

Cover every interactive element (buttons, inputs, links, toggles) and every data-bound region
(lists, counters, status). A static label with no data and no event needs no row. An on-screen
element with no row is a gap; a row with no left-side marker is an orphan - both fail the critic.

## Storyboard structure

- **Left pane** - the screen: Mode B wireframe or Mode A replica/image. Each annotated element
  carries a numbered marker (red circle, white border, centered number).
- **Right pane** - the 5-column table above (No / 구역 / 요소·ID / 설명·동작·데이터·예외), one row
  per marker, in callout order.
- **Board (index)** - a thumbnail grid linking every screen page, so a reader sees the whole set
  and clicks into any screen.

## Production - delegate if storyboard-spec is present, else bundle (standalone)

superpm produces the full 화면설계서 with **no external dependency**. If the richer
`storyboard-spec` skill happens to be installed, hand it the heavy rendering.

1. **Detect.** Check for `~/.claude/skills/storyboard-spec/SKILL.md` (or a `storyboard-spec/`
   skill directory).
2. **If present -> delegate.** Pass it the screen list, the per-screen element tables, and the
   mode. It renders the polished site and adds what superpm's bundle deliberately omits: Figma
   REST auto-extraction (Mode A), headless-Chrome thumbnails + verification screenshots, and
   themeable CSS. Use it; do not re-implement its work.
3. **If absent -> bundle (the default).** Build the document from superpm's self-contained
   templates - zero external CSS/JS, opens straight in a browser:
   - `templates/storyboard-page.html` - copy once per screen; fill the `{{...}}` and replace the
     example wireframe; name it `sb-NN-<slug>.html`. Left = wireframe/replica markup with
     `sb-mark` + `sb-cue` markers; right = the `sb-notes` table.
   - `templates/storyboard-board.html` - the thumbnail/index board linking every page (live
     `<iframe>` thumbnails, so no screenshot step is needed).

The placeholders match storyboard-spec's contract exactly, so a document started standalone
upgrades cleanly if that skill is added later. Either path yields the same artifact shape; only
the rendering polish differs.

## Critic completeness anchors

Every screen has a prev/next (no dead ends); every interactive element has a callout row with at
least an event and an exception; left markers and right rows are 1:1 (no orphans either way); every
data contract is sourced or labeled an assumption; non-happy states (empty / error / loading /
permission) each get a page or a row; the mode (A/B) is stated per screen. A storyboard that
documents only the happy path is incomplete.
