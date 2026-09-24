# Workshop Agent Instructions

You are running a live design workshop. Follow these steps in order.

## Setup

1. Read `setup/install-figma-bridge.md` — install the figma-mcp-bridge fork and Figma plugin.
2. Read `setup/mcp-config-examples.md` — add the MCP server to your agent's config.
3. Read `setup/verify.md` — confirm the bridge works by calling `list_files`.

## Session 1: Photo Marketplace Homepage

4. Read `session-1/phase-1-research.md` — research 4-5 photo marketplace competitors. Write report to `output/research/competitor-analysis.md` using `session-1/report-template.md`.
5. **PAUSE** — present the report. Ask the user to pick 1 competitor as the design reference.
6. Read `session-1/phase-2-tokens.md` — read `assets/DESIGN.md`, create Figma variable collections + text styles via MCP. Screenshot the result to `output/figma/tokens-baseline.png`.
7. **PAUSE** — let the audience see tokens appear live in Figma.
8. Read `session-1/phase-3-build-iterate.md` — build the homepage using the assigned tokens. Iterate 4-5 times. Log each iteration in `output/figma/iteration-log.md` using `session-1/iteration-log-template.md`.

## Session 2: Image Prompts for Placeholders

9. Read `session-2/generate-prompts.md` — find placeholder frames in the Figma file. Craft structured image prompts using `session-2/image-prompt-template.md`. Write prompts to `output/images/prompts.md`.

## Rules

- Always write output files to `output/` directory.
- Use MCP tools directly — call them by name (e.g., `create_frame`, `create_text_style`, `create_variable_collection`).
- If a font fails to load in Figma (e.g., "Fauna One"), fall back to "Playfair Display" for serif titles.
- If Mobbin MCP is not available, use Google search fallback (see phase-1-research.md Path B).
- After each phase, pause and present results before continuing.
- Read `examples/` before producing anything — it defines "good".
- Never invent research, metrics, or references. Use web/MCP tools to gather real material and cite the source URL.