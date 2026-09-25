# Workshop Agent Instructions

You are running a live design workshop. Follow these steps in order.

## Setup

1. Read `setup/install-figma-bridge.md` — install the figma-mcp-bridge fork and Figma plugin.
2. Read `setup/mcp-config-examples.md` — add the MCP server to your agent's config.
3. Read `setup/verify.md` — confirm the bridge works by calling `list_files`.

Phase 1 writes into Figma too, so the bridge must be verified before Session 1 starts — not just before Session 2.

## Session 1: Photo Marketplace Homepage

4. Read `session-1/phase-1-research.md` — research 5 **image-grid marketplace apps** from Mobbin MCP `search_screens`. **Two passes, one time-box (10 min total):** write the report to `output/research/competitor-analysis.md` using `session-1/report-template.md` (7 capped fields), then render that same report as a `Research` page in Figma (one card per reference with a real app screen in a 312×708 slot, `Cross-App Patterns`, `Recommendation`, `Chosen`). **The Figma layout is pre-decided in the render contract at the bottom of `report-template.md` — follow it literally, do not redesign it.**
5. **PAUSE** — present the report and the `Research` page. Ask the user to pick 1 reference as the design reference. Record their pick in both the markdown and the Figma `Chosen` frame.
6. Read `session-1/phase-2-tokens.md` — read `assets/DESIGN.md`, create Figma variable collections + text styles via MCP. Screenshot the result to `output/figma/tokens-baseline.png`.
7. **PAUSE** — let the audience see tokens appear live in Figma.
8. Read `session-1/phase-3-build-iterate.md` — build the homepage using the assigned tokens, comparing each pass against the Phase 1 `Research` page capture. Iterate 4-5 times. Log each iteration in `output/figma/iteration-log.md` using `session-1/iteration-log-template.md`.

## Session 2: Image Prompts for Placeholders

9. Read `session-2/generate-prompts.md` — find placeholder frames in the Figma file. Craft structured image prompts using `session-2/image-prompt-template.md`. Write prompts to `output/images/prompts.md`.

## Rules

- Always write output files to `output/` directory.
- Use MCP tools directly — call them by name (e.g., `create_frame`, `create_text_style`, `create_variable_collection`).
- Research is rendered, not duplicated. Phase 1 researches once and renders it to markdown and Figma; the two must agree. Never re-research to fill a Figma frame.
- Phase 1 is time-boxed to 10 min with a per-step budget table in `phase-1-research.md`. Query Mobbin `search_screens` in **one pass**, extract into **7 capped fields**, render the Figma page **from the pre-decided contract** in `report-template.md`, and verify with **one** end-of-phase visual check. Overwriting prose and re-deriving layout are what made this run 30 minutes.
- **Use case vs. references.** Session 1 *builds* a photo marketplace app; Phase 1 *studies* image-grid marketplace apps. They are deliberately different, because stock-photo apps are nearly absent from Mobbin (1 of 10 named brands has usable screens) while image-grid marketplaces are everywhere. Never pad the report with a near-duplicate to make the category fit.
- **Phase 1 researches mobile, from app screens.** Every capture is a Mobbin app screen at native 1179×2676 (1:2.270). No browser, no viewport config, no desktop pages. Phase 3 builds a 390px frame and holds that width across all iterations.
- **Mobbin returns `[]`?** Try at most **two** query variations, then drop that candidate and take the next. Never retry a dead query, never describe a screen from memory, and name in chat what you dropped.
- Pass **absolute** paths to `save_screenshots` and `create_image`. Relative paths resolve against the MCP server's working directory (the fork clone), not this repo.
- If a font fails to load in Figma (e.g., "Fauna One"), fall back to "Playfair Display" for serif titles.
- If Mobbin MCP is unavailable, degrade per `phase-1-research.md` — wireframe the unfillable slots and label them. There is no Google/web-search path; Mobbin is the only research source.
- If a Mobbin candidate returns `[]` — or the bridge returns nothing usable — draw a wireframe in the same slot and label it `wireframe — capture unavailable`. Never leave an unexplained empty frame, and never fake an image.
- After each phase, pause and present results before continuing.
- Read `examples/` before producing anything — it defines "good".
- Never invent research, metrics, or references. Use web/MCP tools to gather real material and cite the source URL.
- If the Figma bridge is down: Phase 1 degrades (markdown only, say `Figma render skipped — bridge unavailable`), Phases 2 and 3 degrade on their own documented paths. Degrade, don't stall.
