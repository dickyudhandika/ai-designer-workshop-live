# AI Designer Workshop — Live

Run a live design workshop where your AI agent researches competitors, assigns design tokens to Figma, builds a photo marketplace homepage, and generates image prompts — all in real time.

Spawn any MCP-capable agent (Claude Code, Codex, Cursor, Hermes, Windsurf) at this repo and it runs the full workshop end-to-end.

---

## What you need

- **Figma desktop app** (required for dev plugin import)
- **Any MCP-capable AI agent** — Claude Code, Codex, Cursor, Hermes, Windsurf, VS Code Copilot
- **Bun** installed ([bun.sh](https://bun.sh))
- **figma-mcp-bridge fork** — cloned and built (see `setup/`)

Optional but better:
- **Mobbin MCP** — for real competitor app screens (if unavailable, agent falls back to Google search)

---

## Quick start

```
1. Open this folder in your agent.
2. Say: "Read AGENTS.md and run the workshop."
3. Follow the pauses — the agent stops between phases for your input.
```

That's it. The agent reads `AGENTS.md`, installs the bridge, configures MCP, and runs both sessions.

---

## Agenda

### Setup (15 min)

Install the figma-mcp-bridge fork, configure MCP for your agent, verify the connection. See `setup/` for step-by-step instructions covering 6 agents.

### Session 1 — Photo Marketplace Homepage (45 min)

| Phase | Time | What happens |
|---|---|---|
| **Phase 1: Research** | 10 min | Agent researches 4-5 photo marketplace competitors (Mobbin or Google). Produces a pattern analysis report. You pick 1 as the design reference. |
| **Phase 2: Token Assignment** | 10 min | Agent reads `assets/DESIGN.md` and pushes real design tokens into Figma — variable collections, color swatches, named text styles. **This is the "wow" moment** — watch tokens appear live in Figma's sidebar. |
| **Phase 3: Build + Iterate** | 25 min | Agent builds the homepage using the assigned tokens. Iterates 4-5 times, screenshotting and evaluating each pass against the competitor reference. Logs every iteration. |

### Session 2 — Image Prompts for Placeholders (15 min)

Agent reads the Figma file, finds all image placeholder frames, and crafts structured image prompts using the 8-section template. Output is copy-pasteable — paste into your preferred image provider (Midjourney, DALL-E, FAL, whatever).

---

## Repo layout

```
AGENTS.md              ← agent entry point (the conductor)
README.md              ← this file

setup/                 one-time install + MCP config
  install-figma-bridge.md    clone fork, bun build, import Figma plugin
  mcp-config-examples.md     config snippets for 6 agents
  verify.md                  health check (list_files, port 1994)

assets/
  DESIGN.md            baseline design tokens (colors, typography, spacing, components)

session-1/             photo marketplace homepage
  phase-1-research.md        competitor research (Mobbin or Google)
  phase-2-tokens.md          push DESIGN.md tokens to Figma via MCP
  phase-3-build-iterate.md   build homepage + iterate 4-5x
  report-template.md         Phase 1 output format
  iteration-log-template.md  Phase 3 log format

session-2/             image prompts for placeholders
  image-prompt-template.md   8-section structured prompt format
  generate-prompts.md        agent: find placeholders → craft prompts

examples/              what "good" looks like — read before producing
  research/                  example competitor analysis (Shutterstock, Unsplash, Getty, Adobe Stock, Pexels)
  figma/                     example adapted DESIGN.md + iteration log
  images/                    example image prompts for 4 placeholder slots

output/                live session artifacts (gitignored)
  research/                  agent-written reports
  figma/                     screenshots, iteration logs, token exports
  images/                    generated image prompts
```

`examples/` is read-only reference. `output/` is scratch — safe to wipe between workshops.

---

## The fork

This workshop uses [`dickyudhandika/figma-mcp-bridge`](https://github.com/dickyudhandika/figma-mcp-bridge) (branch `feat/create-text-style`), not the upstream `gethopp/figma-mcp-bridge`.

The fork adds 4 tools the upstream lacks:

| Tool | Why we need it |
|---|---|
| `create_variable_collection` | Create Figma variable collections (design tokens) |
| `create_variables` | Batch-create color variables as hex strings |
| `set_bound_variable` | Bind variables to node fields (fill, radius, etc.) |
| `create_text_style` | Create named Figma text styles (H1, Body, Label, etc.) |

Without these, Phase 2 can't push real tokens — you'd get visual swatches only, not actual Figma variables and styles.

---

## License

MIT — see [LICENSE](LICENSE).