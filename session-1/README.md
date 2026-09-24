# Session 1 — Research, Tokens, Build

**45 minutes.** Research a photo marketplace landscape, push `assets/DESIGN.md` into a real Figma file as live tokens, then build and iterate a homepage on those tokens.

---

## What this session is

Session 1 is the proof that an agent can do design work, not design talk. Three phases, each ending in a file on disk. The human steers between phases; the agent proposes and executes.

By the end you have: a competitor analysis grounded in real URLs, a Figma page full of named variables and text styles created over MCP, and a homepage frame at iteration 5 with a written log of what changed at each step.

---

## Agenda

| Min | Phase | What happens | Artifact |
|---|---|---|---|
| 0–10 | **1 — Research** | Agent researches 4–5 photo marketplace competitors (Mobbin MCP if wired, Google if not), extracts layout/nav/color/type/grid patterns, recommends one as the design reference. | `output/research/competitor-analysis.md` |
| 10–20 | **2 — Token Assignment** | Agent reads `assets/DESIGN.md` and creates a "Design System" page in Figma: 9 color variables, color swatches, named text styles, typography scale preview. | `output/figma/tokens-baseline.png` |
| 20–45 | **3 — Build + Iterate** | Agent builds the homepage — nav, hero, category bar, photo grid, featured collection, footer — then iterates 4–5 times against the Phase 1 reference. | `output/figma/iteration-1..5.png` + `output/figma/iteration-log.md` |

Between each phase: **pause.** Present the artifact, let the room react, get a go-ahead. Do not run all three phases without stopping — the pauses are where the workshop happens.

---

## The moment to land (Phase 2)

Phase 2 is the wow moment. The audience watches names appear on the left sidebar of Figma in real time — `background`, `primary`, `border`, then `Title H1`, `Label MD`, `Paragraph SM` — while the agent is still talking.

That sidebar is the point: **a DESIGN.md is a contract, and this is the agent executing it against a real design tool.** Not a screenshot of the tokens, not a JSON export. Actual Figma variables and text styles, bound to actual objects.

Two things worth narrating while it happens:

- The tokens are the *same file* the audience can read. Nothing is hidden in agent memory — `assets/DESIGN.md` is the source of truth and it is 650 lines of YAML + prose anyone can edit.
- The typography conversion is real work: `lineHeight: 1.17` becomes `117 PERCENT`, `letterSpacing: -0.01em` at 48px becomes `-0.48`. The agent does that arithmetic per style, once for every typography token in the file. That's the kind of tedious precision agents are actually good at.

---

## Files in this session

- `README.md` — this file. Human-facing overview.
- `phase-1-research.md` — agent prompt for competitor research. Two paths: Mobbin MCP, or Google fallback.
- `report-template.md` — the exact structure `output/research/competitor-analysis.md` must follow.
- `phase-2-tokens.md` — agent prompt for token assignment. The most detailed prompt in the repo.
- `phase-3-build-iterate.md` — agent prompt for building and iterating the homepage.
- `iteration-log-template.md` — the structure `output/figma/iteration-log.md` must follow.

## Output

- `output/research/competitor-analysis.md` — 4–5 competitors, cross-app patterns, one recommendation
- `output/figma/tokens-baseline.png` — screenshot of the Design System page in Figma
- `output/figma/iteration-1.png` … `iteration-5.png` — one screenshot per iteration
- `output/figma/iteration-log.md` — what was built, evaluated, changed at each iteration

## Reference

- `examples/research/competitor-analysis-example.md` — what a finished Phase 1 report reads like
- `examples/figma/iteration-log-example.md` — what a finished iteration log reads like
- `examples/figma/DESIGN-session-example.md` — what a token session produces, described in prose

---

## Before you start

- Setup complete — figma-mcp-bridge built and connected (see `setup/install-figma-bridge.md`, `setup/verify.md`).
- Figma desktop app open with a file open. An unsaved local file is fine — `fileKey` starting with `unsaved-` still supports all read/write operations.
- The Figma plugin running: **Plugins → Development → Figma MCP Bridge**.
- `assets/DESIGN.md` present. This is the baseline; nobody edits it during the session.

**If the Figma bridge is down:** Phase 1 runs unchanged. Phase 2 and 3 degrade — emit `output/figma/tokens.json` plus HTML/SVG mockups into `output/figma/` with a `SPEC.md` instead of writing into Figma. Say which path you took, in the artifact. Degrade, don't stall.
