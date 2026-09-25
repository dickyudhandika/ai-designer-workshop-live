# AI Designer Workshop — Live

Two sessions. Your AI agent researches, renders into Figma, assigns design tokens, builds and iterates a product — while the room watches.

Spawn any MCP-capable agent (Claude Code, Codex, Cursor, Hermes, Windsurf) at this repo. It installs the tooling first, then you drive both sessions by reading the files below and telling it what to do.

---

## Prerequisites

- **Figma desktop app** — required for dev plugin import
- **Bun** — for building the Figma bridge ([bun.sh](https://bun.sh))
- **Any MCP-capable AI agent**
- **Mobbin MCP** — the research source for Session 1

---

## Run order

```
1. Open this folder in your agent.
2. Say: "Read AGENTS.md and set up the workshop."
3. Let it install and verify the Figma bridge. It will stop when ready.
4. Read session-1.md and drive your agent through it.
5. Read session-2.md and drive your agent through it.
```

`AGENTS.md` is install-only — it stops and waits once the bridge is verified. Every step after that is yours to call.

---

## Session 1 — Build an AI photostock for designers

**Case study: a polished AI photostock product for the next design project.**

`session-1.md` walks the room through seven steps:

1. Frame the case study
2. Research layouts with Mobbin via MCP
3. Pick 1–3 references you love — with reasons
4. Merge the concepts and go lo-fi: 1–4 quick variations
5. Pick the best one
6. Assign your design tokens to it
7. Inspect what the tokens improved and what they broke

The arc: research on real data → several rough directions → one choice → a real token system applied to it. By step 7 the room sees the difference tokens make, on a design they watched get built.

## Session 2 — Make it sellable

`session-2.md` is the last step: fill the image placeholders so the thing can actually be bought.

Each placeholder gets a structured eight-section prompt, written for that slot's job — hero, grid card, curated set, category thumbnail. **The format is the deliverable**, and it's provider-neutral: paste it into Midjourney, Nano Banana, DALL·E, FAL, Ideogram, Firefly, or a local model.

If you want your agent to write those prompts from a reference image, or generate the images itself, install the `/aimg` skill — see `setup/aimg.md`. Works on any agent; optional either way.

---

## Repo layout

```
AGENTS.md              install-only — Figma bridge setup + verification
README.md              this file
session-1.md           run sheet: research → lo-fi → tokens
session-2.md           run sheet: images into placeholders

setup/                 install detail
  install-figma-bridge.md     clone fork, bun build, import Figma plugin
  mcp-config-examples.md      MCP config snippets for 6 agents
  verify.md                   health check
  aimg.md                     optional /aimg image-generation shortcut (Hermes)

assets/
  DESIGN.md            baseline design tokens — the source for Session 1 step 6

output/                scratch artifacts (gitignored)
```

`assets/DESIGN.md` is the token source. It is not a template — it is the contract the agent executes against Figma in step 6.

---

## The fork

This workshop uses [`dickyudhandika/figma-mcp-bridge`](https://github.com/dickyudhandika/figma-mcp-bridge) (branch `feat/create-text-style`), not upstream `gethopp/figma-mcp-bridge`.

The fork adds 4 tools the npm package lacks:

| Tool | Why |
|---|---|
| `create_variable_collection` | Create Figma variable collections (design tokens) |
| `create_variables` | Batch-create color variables as hex strings |
| `set_bound_variable` | Bind variables to node fields (fill, radius, padding, …) |
| `create_text_style` | Create named Figma text styles |

Without these, step 6 can only draw swatches — not real Figma variables and styles.

---

## License

MIT — see [LICENSE](LICENSE).
