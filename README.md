# AI Designer Workshop — Live

Run a live design workshop driven by any MCP-capable AI agent.

This repo is a self-contained harness: point an agent at `AGENTS.md`, give it a brief,
and it runs a real design session — research → references → visual direction → Figma/export —
writing artifacts into `output/` as it goes. No app, no build step. Markdown + folders + an agent.

---

## What you need

- Any MCP-capable agent (Claude Code, Cursor, Codex, Hermes, …)
- Optional MCP servers, wired in the agent, for the live parts:
  - **Research / web** — competitor + reference gathering
  - **Image generation** — moodboards, visual concepts
  - **Figma** — write frames/pages into a real file during the session

Everything degrades gracefully. No Figma MCP? Agent exports HTML/SVG into `output/figma/`.
No image MCP? Agent writes prompts into `output/images/prompts.md`.

---

## Quickstart

```
1. Open this folder in your agent.
2. Say: "Read AGENTS.md, then run Session 1 for this brief: <your brief>."
3. Watch artifacts land in output/. Ship the useful ones.
```

---

## Repo layout

```
AGENTS.md          agent operating instructions (the important file)
README.md          this file
LICENSE

setup/             one-time environment + MCP wiring notes
session-1/         session 1 script, prompt, agenda, materials
session-2/         session 2 script, prompt, agenda, materials

examples/          worked reference output — what "good" looks like
  research/        example research synthesis
  images/          example moodboard prompts + exports
  figma/           example frame structure / handoff spec

output/            live session artifacts land here
  research/        agent-written research
  images/          agent-generated visuals
  figma/           agent-written frames / specs

assets/            logos, fonts, brand inputs, screenshots
```

`examples/` is read-only reference. `output/` is scratch — safe to wipe between sessions.

---

## Sessions

**Session 1 — Understand & aim.** Brief intake, landscape research, reference collection,
moodboard, 2–3 visual directions. Output: a chosen direction with rationale and references.

**Session 2 — Design & hand off.** Take the chosen direction, build the screens in Figma,
produce a token/component pass and a handoff spec. Output: a Figma artifact + a written spec
a developer can build from.

Each session folder holds the agenda, the agent prompt, and the presenter script.

---

## Rules that make it work

- **Artifacts over chat.** Every step ends in a file in `output/`. If it's not on disk, it didn't happen.
- **References before opinions.** The agent gathers real references before proposing direction.
- **One direction wins.** The agent recommends; the human decides. No hedging across three options.
- **Human in the loop.** Live means the human steers between phases, not only at the end.

---

## License

MIT — see [LICENSE](LICENSE).
