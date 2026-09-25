# AI Designer Workshop — Live

Two sessions. Your AI agent researches, renders into Figma, assigns design tokens, builds and iterates a product — while the room watches.

The product is an **AI photostock for designers**: images better than they could afford to commission, so their work looks more expensive and they charge accordingly. That commercial job is the brief the whole session designs against.

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

**Setup has two tiers**, both in `setup/verify.md`:

- **Primary — required.** The Figma bridge: six checks. Nothing in Session 1 works until they all pass.
- **Optional — verified separately.** The `/aimg` skill (image prompts). Session 2 works without it.

---

## Session 1 — Build an AI photostock for designers

**The brief: sell images to designers, and make their work look more expensive.**

A mobile app where designers search, browse and buy AI-generated imagery. It's aimed at designers whose fee scales with how good their work looks — and who today either pay for a shoot or use free stock that makes everything around it look cheap. The promise is images better than they could afford to commission, so they ship premium work and charge accordingly.

That promise is the design brief: not a gallery, a shop that has to feel like an upgrade.

`session-1.md` walks the room through seven steps:

1. Set the brief — who buys, and why
2. Research layouts with Mobbin via MCP
3. Pick 1–3 references you love — with reasons
4. Merge the concepts and go lo-fi: 2–4 variations, each a different reason to buy
5. Pick the best one
6. Assign your design tokens to it
7. Inspect what the tokens improved and what they broke

The arc: research on real data → several rough directions → one choice → a real token system applied to it. By step 7 the room sees the difference tokens make, on a design they watched get built.

## Session 2 — Write the prompts that sell the images

`session-2.md` is the last step: every image placeholder gets a written prompt, collected in `prompts.md`, ready to paste into your own provider.

**Prompts, not images.** The agent writes the prompt and stops — generation, model choice and credits stay yours. The eight-section format is provider-neutral: Midjourney, Nano Banana, DALL·E, FAL, Ideogram, Firefly, local.

**Written to the brief, not to beauty.** The product promises imagery better than a designer could afford — an image that looks like free stock breaks the promise on the one screen meant to sell it.

Install the `/aimg` skill if you want your agent to scan a reference image into that format in one step — see `setup/aimg.md`. Works on any agent; optional.

---

## Repo layout

```
AGENTS.md              install-only — Figma bridge setup + verification
README.md              this file
session-1.md           run sheet: research → lo-fi → tokens
session-2.md           run sheet: image prompts into placeholders

setup/                 install detail
  install-figma-bridge.md     clone fork, bun build, import Figma plugin
  mcp-config-examples.md      MCP config snippets for 6 agents
  verify.md                   verification, two tiers: primary (bridge) + optional (aimg)
  aimg.md                     optional /aimg image-prompt skill (any agent)

skills/
  aimg/SKILL.md        portable SKILL.md — scan image → 8-section prompt → clipboard

assets/
  DESIGN.md            baseline design tokens — the source for Session 1 step 6
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
