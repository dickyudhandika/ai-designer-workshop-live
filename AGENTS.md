# Workshop Agent Instructions

Install-only. Set up the Figma bridge, verify it, then stop and wait for the human.

---

## 1. Install Bun (skip if present)

```bash
bun --version || curl -fsSL https://bun.sh/install | bash
```

## 2. Clone the fork

```bash
cd ~/Downloads && git clone -b feat/create-text-style https://github.com/dickyudhandika/figma-mcp-bridge.git
```

## 3. Build server + plugin

```bash
cd ~/Downloads/figma-mcp-bridge && bun install
cd server && bun install && bun run build
cd ../plugin && bun install && bun run build
```

## 4. Import the plugin into Figma

Figma **desktop** app → open any file → **Plugins → Development → Import plugin from manifest…** → select `~/Downloads/figma-mcp-bridge/plugin/manifest.json` → run it.

Keep the plugin window open. The bridge only sees files where it's running.

## 5. Add the MCP server

Point the agent's config at the **built fork**, not the npm package:

```json
{
  "mcpServers": {
    "figma-bridge": {
      "command": "node",
      "args": ["/Users/<you>/Downloads/figma-mcp-bridge/server/dist/index.js"]
    }
  }
}
```

Per-agent snippets (Claude Desktop, Claude Code, Cursor, Windsurf, Codex, VS Code, Hermes): `setup/mcp-config-examples.md`. Then **fully restart the agent.**

## 6. Verify — primary tier, all six must pass

Work down this table. **Don't start Session 1 until all six pass** — a half-connected bridge fails silently and burns workshop time.

| # | Check | Expected |
|---|---|---|
| 1 | `lsof -i :1994` | `node` LISTENing on 1994 |
| 2 | agent lists MCP tools | `create_variable_collection`, `create_variables`, `set_bound_variable`, `create_text_style` present |
| 3 | `list_files` | array with `fileKey` + `fileName` |
| 4 | `get_metadata` on that key | file name, pages, current page |
| 5 | `create_frame` 100×100 `fillHex: "#1A5EFF"` | frame appears in Figma — delete after |
| 6 | `save_screenshots` on it, **absolute** `outputPath` | PNG exists at that path |

Missing tool in #2 → config points at the npm package. Empty #3 → plugin isn't running. `unsaved-` fileKey is fine — everything still works.

Full detail for every check, plus the fork-specific write tests: `setup/verify.md`.

---

## 7. Optional — install the `/aimg` skill

Skip this and everything still works. Install it if you want your agent to turn a reference image into a reusable prompt in one step.

**It writes prompts. It does not generate images** — that stays the human's call, and they take the prompts to their own provider.

The skill ships in this repo at `skills/aimg/SKILL.md`. Plain `SKILL.md`, no build step.

### Install it

Say this to your agent:

> Install the `/aimg` skill. Copy `skills/aimg/` from this repo into your own skills folder, then confirm you can see it.

`~/.agents/skills/` is the cross-agent convention — Codex, Cursor, Gemini CLI and most skill loaders read it directly:

```bash
mkdir -p ~/.agents/skills && cp -R "$(pwd)/skills/aimg" ~/.agents/skills/aimg
```

Some agents only scan their own folder. Symlink it across instead — Claude Code and Cursor both follow symlinks, so one copy stays the source of truth:

```bash
ln -sfn ~/.agents/skills/aimg ~/.claude/skills/aimg    # Claude Code
ln -sfn ~/.agents/skills/aimg ~/.cursor/skills/aimg    # Cursor
ln -sfn ~/.agents/skills/aimg ~/.codex/skills/aimg     # Codex
```

**Hermes** already keeps its own at `~/.hermes/skills/devops/aimg/`.

Then restart the agent so it picks the skill up. There's nothing else to configure — no image provider needed.

### Verify it

```bash
ls -la ~/.agents/skills/aimg/SKILL.md
```

Then ask your agent: *"do you have the aimg skill, and what does it do?"* It should find the skill and describe scanning an image into the eight-section format. Not found → restart the agent; still missing → see `setup/aimg.md`.

### What it makes your agent do

Hand it a reference image and say *"scan this into a prompt"*. Three steps:

1. **Look at the image** — read the actual pixels, not a remembered description.
2. **Scan it** against the eight-section format: `TYPE & SUBJECT`, `SUBJECT ACTION`, `ENVIRONMENT`, `LIGHTING`, `CAMERA`, `TEXTURE & PROPS`, `STYLE KEYWORDS`, `CONSTRAINTS`.
3. **Copy the whole filled block to the clipboard** (`pbcopy`), ready to paste into Midjourney, Nano Banana, or whatever you use.

Then it stops. It's told not to generate — not a placeholder, not a mock, not an SVG stand-in.

---

## Stop here

Once the **six primary checks** pass, tell the human you're ready and wait. Install `/aimg` only if they ask for it. The rest of the workshop is driven by them from `session-1.md` and `session-2.md`.

More detail — port conflicts, rebuild rules, symptom→fix table: `setup/install-figma-bridge.md` and `setup/verify.md`.
