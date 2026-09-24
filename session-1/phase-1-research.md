# Phase 1 — Competitor Research

Agent prompt. **10 minutes.** Read `session-1/report-template.md` before writing anything — that file defines the output structure.

---

## Goal

Find 4–5 real photo marketplace / microstock apps and websites. Extract how each one lays out its home screen. Synthesize cross-app patterns. Recommend **one** as the design reference for Phase 3.

Two paths. Take Path A if Mobbin MCP is wired in your agent, Path B otherwise. Both produce the same artifact.

---

## Path A — Mobbin MCP (if available)

Use Mobbin as the screen source. Queries:

1. `"photo marketplace app home screen with grid"`
2. `"microstock photography app browse page"`

Parameters on both: `platform: ios`, `limit: 12`.

Then:

1. Scroll the results and pick **4–5 distinct apps** — different companies, not four versions of the same app.
2. For each app, open the home/browse screen and extract the fields listed under **Extraction Fields** below.
3. Note the screen URL or app slug next to each competitor so the audience can verify.

If Mobbin returns fewer than 4 usable apps, supplement with Path B rather than padding the report with near-duplicate screens.

---

## Path B — Google search (default fallback)

Search Google for:

- `"photo marketplace app homepage design"`
- `"microstock website homepage layout"`

Pull the top results from the actual photo marketplaces — Shutterstock, Getty Images, Unsplash, Pexels, Adobe Stock, iStock, EyeEm, Alamy, Depositphotos, Dreamstime. Pick **4–5 distinct sites**.

For each: visit the live homepage and extract the fields below from what is actually on the page. If a site is unreachable, drop it and name the gap in the report — do not describe it from memory.

---

## Extraction Fields

Same fields for both paths. These are the things Phase 3 will be built against, so be concrete.

| Field | What to record |
|---|---|
| **Layout structure** | Section order top to bottom, hero treatment, how the fold is used |
| **Navigation** | Top bar vs. sidebar vs. bottom tabs; what's in the nav; logo placement |
| **Color usage** | Base/background color, accent color and where it's allowed to appear, how photos sit against the canvas |
| **Typography hierarchy** | Display vs. body faces, how many sizes are visible, where weight changes |
| **Primary action** | The single most important button on the screen — what it says and where it sits |
| **Grid type** | Masonry, uniform, fixed columns, mixed; gutter behavior |
| **Search prominence** | High/medium/low + placement (in nav? in hero? full-width?) |
| **Filters** | Placement + style (chips, sidebar, sheet, inline dropdown) |
| **What works** | 1–2 bullets, specific (e.g. "price sits on the card, no click required") |
| **What's weak** | 1–2 bullets, specific (e.g. "hero carousel auto-advances before you can read it") |

Also note **where the images themselves come from** — infinite scroll, curated collections, algorithmic rows — since that shapes the Phase 3 grid.

---

## Synthesis Rules

- **A pattern in 3+ competitors is an industry standard.** Say so. Phase 3 inherits it unless there's a reason not to.
- **A pattern only one competitor does well is a differentiator.** Flag it as an opportunity.
- **A repeated complaint-shaped weakness is an opportunity.** If three sites bury search, that's a design decision worth making deliberately.
- Never invent a competitor, a screen, or a metric. Every claim carries a URL or a Mobbin app slug.

---

## Output

Write to `output/research/competitor-analysis.md` using the structure in `session-1/report-template.md`. Do not rename, reorder, or drop sections.

The report must end with a **Recommendation**: one competitor, named, with 2–3 sentences grounding the choice in the research above — not in taste.

---

## MCP / tools used

- `mobbin` search + screen detail (Path A)
- web search + page extract (Path B)
- `write_file` — the artifact

## Then: PAUSE

Present the report. Summarize in three lines: who was researched, what the cross-app pattern is, who you recommend.

**Stop. Let the human pick the reference.** They may override your recommendation — that's their call and the session continues with their pick. Record the choice in the report (append a `**Chosen:**` line under the Recommendation) before moving to Phase 2.

## Done when

- `output/research/competitor-analysis.md` exists
- 4–5 competitors, each with a URL or app slug and all extraction fields filled
- Cross-app patterns section lists at least 3 patterns
- Recommendation names exactly one competitor
- The human's choice is on record
