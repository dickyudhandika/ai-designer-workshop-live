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

## 6. Verify — all six must pass

| # | Check | Expected |
|---|---|---|
| 1 | `lsof -i :1994` | `node` LISTENing on 1994 |
| 2 | agent lists MCP tools | `create_variable_collection`, `create_variables`, `set_bound_variable`, `create_text_style` present |
| 3 | `list_files` | array with `fileKey` + `fileName` |
| 4 | `get_metadata` on that key | file name, pages, current page |
| 5 | `create_frame` 100×100 `fillHex: "#1A5EFF"` | frame appears in Figma — delete after |
| 6 | `save_screenshots` on it, **absolute** `outputPath` | PNG exists at that path |

Missing tool in #2 → config points at the npm package. Empty #3 → plugin isn't running. `unsaved-` fileKey is fine — everything still works.

---

## Stop here

Once all six pass, tell the human you're ready and wait. The rest of the workshop is driven by them from `session-1.md` and `session-2.md`.

More detail — port conflicts, rebuild rules, symptom→fix table: `setup/install-figma-bridge.md` and `setup/verify.md`.
