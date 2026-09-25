# Phase 3 — Build Photo Marketplace Homepage + Iterate

Agent prompt. **25 minutes.** Read `session-1/iteration-log-template.md` before you start logging. Read `output/research/competitor-analysis.md` for the reference the human picked — and open the `Research` page in Figma beside it. The page carries the app screens; that's what you're comparing against, not your memory of the descriptions.

---

## Goal

Build a photo marketplace app homepage in Figma using the tokens assigned in Phase 2. Iterate 4–5 times, each pass measured against the reference chosen in Phase 1.

**The reference is an image-grid marketplace app, not a photo marketplace.** It was studied because it solved the same design problem at 390px — a mobile homepage whose job is to show a searchable grid of photographs. What transfers is the structure: search prominence, grid density, bottom-bar behaviour, thumb reach. What does *not* transfer is its content model — Depop's price/brand/size metadata is not the photo marketplace's metadata. Inherit the layout decisions, adapt the tile contents.

---

## Homepage structure

A photo marketplace **mobile** homepage typically carries:

1. **Top bar** — logo, search (field or icon), one utility control. Nothing else fits at 390px.
2. **Hero / opening statement** — one line of copy, or skip it and go straight to the grid
3. **Category chips** — horizontal scroll, never wrapping (Nature, People, Business, Food, Architecture…)
4. **Photo grid** — 2-column masonry or uniform cards, with title, photographer, price
5. **Featured collection** — one curated band, if the first screen can afford it
6. **Bottom bar / footer** — tab bar, email capture, links, copyright

**This is the mobile list, and it is shorter than a desktop one on purpose.** At 390px you cannot have
a nav *and* a hero *and* three merchandising bands before the first photo — that is exactly what the
Phase 1 research penalised. The chosen reference's mobile layout outranks this list: if the reference
does something better, do that instead, and say so in the log.

**What Phase 1 found, and what that means for the build:**

- **Search is the primary object.** Every reference gives it the widest control on screen or a hero
  position. At 390px that means a full-width field, not a collapsed icon you have to hunt for.
- **Two columns, not one.** 3 of 5 use a 2-column grid at mobile width. One column reads as an
  article, not a marketplace.
- **Nobody anchors anything to the thumb.** All 5 keep every control in the top third. The bottom third
  of an 844px screen is the comfortable one-handed zone — and it is empty on all five. This is the
  clearest unclaimed position in the category, and this build should take it.
- **One accent, one CTA.** Phase 2's `primary` is for the single most important action. Two blue things
  means one is wrong.

Depop — the recommendation — is a marketplace with sellers, so expect a sell/list action in its bottom
bar. The photo marketplace has the same shape (photographers upload, buyers browse), so carrying a
single commerce action in the thumb zone is a legitimate inheritance. Don't also inherit a promo
banner; that was the reference's weakness, not its strength.

---

## Iteration protocol

Every iteration runs the same five steps. Don't skip the screenshot or the log; the log is the artifact.

1. **Build** — `create_frame`, `create_text`, `create_shape`, `set_solid_fill`, `set_auto_layout`. Bind colors to variables with `set_bound_variable` wherever the tool allows.
2. **Screenshot** — `save_screenshots` on the homepage frame, `outputPath` = `output/figma/iteration-N.png`.
3. **Evaluate** — compare against the Phase 1 reference. Put the `Research` page's app screen for the chosen reference beside your iteration screenshot; compare the two images, not your recollection of the report:
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
| 1 | **Structure + layout** | The skeleton — top bar, hero line, category chips, 2-column grid, featured band, bottom bar. Gray placeholder rectangles for every image. |
| 2 | **Token application** | All colors come from variables, not raw hex. Typography uses the named text styles. Spacing is on the 4px scale. |
| 3 | **Content refinement** | Real-ish copy — no "Lorem ipsum". Search with placeholder text. Category chips with real names. Cards with title + photographer + price. |
| 4 | **Visual polish + thumb reach** | 1px `border` separation, `primary` CTA placement, nav density, alignment — and check what sits in the bottom third of the frame. |
| 5 | **Final review** | Full-page screenshot. Side-by-side against the chosen reference's **app screen**. Name the remaining gaps honestly. |

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
- **Page width — 390px, mobile.** Hold it across all iterations so screenshots stay comparable and so they match the Phase 1 app screens. Build the frame at **390 × 844** (the device viewport); if the page runs longer than one screen, let the frame run taller and keep the width fixed — the first 844px is the fold, and that is the band Phase 1 measured.
- **Two-column grid.** 3 of the 5 researched references use 2 columns at mobile width. One column reads as an article.
- **Put the primary action where the thumb is.** The bottom third of the frame is the comfortable one-handed zone and every researched reference leaves it empty. Search, or the single `primary` CTA, belongs there — that is the deliberate break from the category.

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
