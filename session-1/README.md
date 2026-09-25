# Session 1 — Research, Tokens, Build

**45 minutes.** Research a photo marketplace landscape, render that research as a visual `Research` page in Figma, push `assets/DESIGN.md` into the same file as live tokens, then build and iterate a homepage on those tokens.

---

## What this session is

Session 1 is the proof that an agent can do design work, not design talk. Three phases, each ending in something the audience can look at. The human steers between phases; the agent proposes and executes.

**The use case is a photo marketplace app. The references are image-grid marketplace apps.** That gap is deliberate: of ten named stock-photo brands, one has usable app screens on Mobbin, while image-grid marketplaces (Depop, Etsy, Vinted…) are everywhere. Phase 1 studies the apps that already solved "a mobile homepage showing a searchable grid of photographs"; Phase 3 builds the photo marketplace on those decisions.

By the end you have: a competitor analysis grounded in real URLs — on disk *and* on a Figma page with real homepage screenshots — a Figma page full of named variables and text styles created over MCP, and a homepage frame at iteration 5 with a written log of what changed at each step.

The through-line: **three sources of truth, each one a step more real than the last.** Research starts as markdown, becomes a Figma page. `assets/DESIGN.md` starts as a file, becomes Figma variables. The homepage starts as frames, becomes an iterated design. Nothing lives only in the agent's head.

---

## Agenda

| Min | Phase | What happens | Artifact |
|---|---|---|---|
| 0–10 | **1 — Research** | Agent queries Mobbin `search_screens` for 5 **image-grid marketplace apps** (Depop, Etsy, Vinted, Vestiaire Collective, Nextdoor), extracts layout/nav/grid/action/mobile-pattern into 7 capped fields, recommends one as the design reference. Then renders it as a `Research` page in Figma — one card per reference with a real app screen. Time-boxed; see the budget table in `phase-1-research.md`. | `output/research/competitor-analysis.md` + `Research` page in Figma + `output/figma/research-page.png` |
| 10–20 | **2 — Token Assignment** | Agent reads `assets/DESIGN.md` and creates a "Design System" page in Figma: 9 color variables, color swatches, named text styles, typography scale preview. | `output/figma/tokens-baseline.png` |
| 20–45 | **3 — Build + Iterate** | Agent builds the **mobile** homepage in a 390px frame — top bar, hero line, category chips, 2-column grid, featured band, bottom bar — then iterates 4–5 times against the Phase 1 reference. | `output/figma/iteration-1..5.png` + `output/figma/iteration-log.md` |

Between each phase: **pause.** Present the artifact, let the room react, get a go-ahead. Do not run all three phases without stopping — the pauses are where the workshop happens.

---

## The moment to land (Phase 2)

Phase 2 is the wow moment. The audience watches names appear on the left sidebar of Figma in real time — `background`, `primary`, `border`, then `Title H1`, `Label MD`, `Paragraph SM` — while the agent is still talking.

That sidebar is the point: **a DESIGN.md is a contract, and this is the agent executing it against a real design tool.** Not a screenshot of the tokens, not a JSON export. Actual Figma variables and text styles, bound to actual objects.

Two things worth narrating while it happens:

- The tokens are the *same file* the audience can read. Nothing is hidden in agent memory — `assets/DESIGN.md` is the source of truth and it is 650 lines of YAML + prose anyone can edit.
- The typography conversion is real work: `lineHeight: 1.17` becomes `117 PERCENT`, `letterSpacing: -0.01em` at 48px becomes `-0.48`. The agent does that arithmetic per style, once for every typography token in the file. That's the kind of tedious precision agents are actually good at.

## The quieter moment to land (Phase 1)

Phase 1 has the same shape, one step earlier and with no token system to lean on. The agent queries Mobbin, and the output lands as a Figma page: five cards, five real app screens from five real references, then a patterns block and a recommendation with a blue left edge.

Worth narrating:

- **It's the same research, rendered twice.** The markdown is written first, then the Figma page is built *from* it. The two must agree — the agent isn't re-researching, it's rendering.
- **The layout is pre-decided, and that's the point.** `report-template.md` carries a render contract — the exact node tree, the accent-panel construction, the fills and spacing. The agent transcribes into it instead of designing it live. That contract is why this phase takes 10 minutes instead of 30.
- **The fields are capped.** 7 capped observation fields, 120–200 characters each. The caps force specificity: a claim that fits in one line is a claim the agent actually verified.
- **The reference set is chosen for coverage, not for the category.** Stock-photo apps barely exist on Mobbin — one of ten named brands. The agent studies image-grid marketplaces instead: same design problem (a searchable photo grid on a phone), far better evidence. Say that out loud; it's the honest finding and a real research skill.
- **Every screen is the home screen**, picked deliberately out of the several Mobbin returns per app — not result 0 blindly. One ratio across all five (native 1:2.270) so the row reads as comparable evidence rather than five random crops.
- **Fallbacks are named, not hidden.** Mobbin down, or a candidate returns `[]` twice? The frame gets a wireframe drawn from the recorded layout and a label saying so. An agent that quietly ships an empty box is worse than one that says what it couldn't do.

Phase 1 runs *before* Phase 2 creates the variables, so it uses raw hex from `assets/DESIGN.md`. Say that out loud — it sets up Phase 2, where raw values become a named system.

---

## Files in this session

- `README.md` — this file. Human-facing overview.
- `phase-1-research.md` — agent prompt for competitor research. Mobbin `search_screens` is the only path; two output passes (markdown, then Figma render).
- `report-template.md` — the exact structure for both Phase 1 artifacts: `output/research/competitor-analysis.md`, and the Figma `Research` page that mirrors it. 7 capped fields, plus the **render contract** — the pre-decided Figma node tree with the 312×708 portrait slot, accent-panel construction, fills, spacing, and the layout mechanics that used to cost a rebuild each. Includes the screenshot rules.
- `phase-2-tokens.md` — agent prompt for token assignment. The most detailed prompt in the repo.
- `phase-3-build-iterate.md` — agent prompt for building and iterating the homepage.
- `iteration-log-template.md` — the structure `output/figma/iteration-log.md` must follow.

## Output

- `output/research/competitor-analysis.md` — 5 references, 7 capped fields each, cross-app patterns, one recommendation
- `output/research/screens/*.png` — one Mobbin app screen per reference
- **Figma → page `Research`** — one frame per reference + `Cross-App Patterns` + `Recommendation` + `Chosen`
- `output/figma/research-page.png` — screenshot of the `Research` page
- `output/figma/tokens-baseline.png` — screenshot of the Design System page in Figma
- `output/figma/iteration-1.png` … `iteration-5.png` — one screenshot per iteration
- `output/figma/iteration-log.md` — what was built, evaluated, changed at each iteration

## Reference

- `examples/research/competitor-analysis-example.md` — what a finished Phase 1 report reads like. This is the *content* standard; the Figma page mirrors its structure.
- `examples/figma/iteration-log-example.md` — what a finished iteration log reads like
- `examples/figma/DESIGN-session-example.md` — what a token session produces, described in prose

---

## Before you start

- Setup complete — figma-mcp-bridge built and connected (see `setup/install-figma-bridge.md`, `setup/verify.md`).
- Figma desktop app open with a file open. An unsaved local file is fine — `fileKey` starting with `unsaved-` still supports all read/write operations.
- The Figma plugin running: **Plugins → Development → Figma MCP Bridge**.
- `assets/DESIGN.md` present. This is the baseline; nobody edits it during the session.
- **`list_files` works.** Phase 1 now depends on the bridge as much as Phase 2 does — verify before the room is watching (see `setup/verify.md`).

**If the Figma bridge is down:** Phase 1 degrades — write `output/research/competitor-analysis.md` normally and say `Figma render skipped — bridge unavailable.` Skip the research render entirely; do not fake frames or substitute an HTML page. Phase 2 and 3 degrade on their own documented path (emit `output/figma/tokens.json` plus HTML/SVG mockups into `output/figma/` with a `SPEC.md` instead of writing into Figma). A dead bridge costs you Figma in all three phases — it never ends the session. Degrade, don't stall.
