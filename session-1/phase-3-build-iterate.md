# Phase 3 — Build Photo Marketplace Homepage + Iterate

Agent prompt. **25 minutes.** Read `session-1/iteration-log-template.md` before you start logging. Read `output/research/competitor-analysis.md` for the reference the human picked.

---

## Goal

Build a photo marketplace app homepage in Figma using the tokens assigned in Phase 2. Iterate 4–5 times, each pass measured against the competitor chosen in Phase 1.

---

## Homepage structure

A photo marketplace homepage typically carries:

1. **Top nav bar** — logo, search bar, nav links, upload button, user avatar
2. **Hero section** — headline, subheadline, CTA, featured photo or collage
3. **Category chips** — horizontal scrollable categories (Nature, People, Business, Food, Architecture…)
4. **Photo grid** — masonry or uniform grid of photo cards with title, photographer, price
5. **Featured collection** — curated set with editorial framing
6. **Newsletter / footer** — email capture, links, copyright

Adjust against the chosen reference. If the reference does something better, do that instead — and say so in the log.

---

## Iteration protocol

Every iteration runs the same five steps. Don't skip the screenshot or the log; the log is the artifact.

1. **Build** — `create_frame`, `create_text`, `create_shape`, `set_solid_fill`, `set_auto_layout`. Bind colors to variables with `set_bound_variable` wherever the tool allows.
2. **Screenshot** — `save_screenshots` on the homepage frame, `outputPath` = `output/figma/iteration-N.png`.
3. **Evaluate** — compare against the Phase 1 reference:
   - Does the hierarchy match? (search prominence, CTA placement)
   - Does the grid feel right? (spacing, card sizing, gutters)
   - Are tokens used correctly? (`primary` for CTAs only, `border` for separation only)
   - What's missing or weak?
4. **Improve** — apply the specific fixes. No vague polish passes.
5. **Log** — append to `output/figma/iteration-log.md` using `session-1/iteration-log-template.md`.

---

## Iteration focus areas

| # | Focus | What to get right |
|---|---|---|
| 1 | **Structure + layout** | The skeleton — nav, hero, category bar, grid, featured, footer. Gray placeholder rectangles for every image. |
| 2 | **Token application** | All colors come from variables, not raw hex. Typography uses the named text styles. Spacing is on the 4px scale. |
| 3 | **Content refinement** | Real-ish copy — no "Lorem ipsum". Search bar with placeholder text. Category chips with real names. Cards with title + photographer + price. |
| 4 | **Visual polish** | Card shadows, 1px `border` separation, `primary` CTA placement, nav density, alignment. |
| 5 | **Final review** | Full-page screenshot. Side-by-side against the competitor reference. Name the remaining gaps honestly. |

---

## Rules

Hard rules. Breaking one is a failed phase.

- **Use Phase 2 tokens. Never raw hex.** Every fill, text color, and border resolves to a variable via `set_bound_variable` where possible. If you must use a raw value because the tool can't bind there, log it.
- **One H1 per page** — the hero headline. Nothing else uses `Title H1`.
- **`primary` (#1A5EFF) for the single most important CTA only.** If two things are blue, one of them is wrong. `destructive` appears only on error/destructive UI, which this page probably doesn't have.
- **`border` separates content, never decorates.** No border for emphasis; use `muted` backgrounds for section separation instead.
- **All radius 0px.** Sharp edges are the aesthetic. If a corner is rounded, fix it.
- **4px spacing grid.** Use the DESIGN.md scale only: 4, 8, 12, 16, 24, 32, 48, 64. No invented values like 20 or 30.
- **Placeholder images** = gray rectangles filled `#F3F1EB` (`muted`) with `IMAGE PLACEHOLDER` text inside. Session 2 replaces these with generated image prompts. Name them `placeholder` or `image-*` so Session 2 can find them — the naming is load-bearing.
- **Page width** — pick a fixed frame width (e.g. 1440 wide desktop, or a 390-wide mobile frame per the reference) and hold it across all iterations so screenshots are comparable.

---

## Output

- `output/figma/iteration-1.png` … `output/figma/iteration-5.png`
- `output/figma/iteration-log.md` — all 5 iterations logged, using the template

## MCP tools used

`create_page`, `create_frame`, `create_text`, `create_shape`, `set_solid_fill`, `set_auto_layout`, `set_bound_variable`, `get_screenshot`, `save_screenshots`

## Then: PAUSE

Present iteration 5. Three lines: what the homepage does well, where it still falls short of the reference, what Session 2 will fix (the placeholders).

Stop. Do not start Session 2 without a go-ahead.

## Done when

- Homepage frame exists in Figma, fully built, tokens bound
- 5 screenshots on disk
- `output/figma/iteration-log.md` has 5 entries with evaluations and specific changes
- The placeholder count is known and stated — Session 2 depends on it
