# Install Figma MCP Bridge (Workshop Fork)

The stock npm package (`@gethopp/figma-mcp-bridge`) is **read-only**. This workshop
needs to *write* design tokens into Figma, so we use a fork that adds four authoring
tools on top of upstream:

| Tool | What it does |
| --- | --- |
| `create_variable_collection` | Create a local variable collection (design tokens). Returns the default mode ID. |
| `create_variables` | Batch-create variables in a collection. `COLOR` accepts a hex string. |
| `set_bound_variable` | Bind a variable to a node field (`fill`, `cornerRadius`, `padding*`, `width`, …). Omit `variableId` to unbind. |
| `create_text_style` | Create a named text style (font, size, line height, letter spacing, optional variable bindings). |

Everything upstream (reading files, creating frames, screenshots) works unchanged.

- Fork: `https://github.com/dickyudhandika/figma-mcp-bridge`
- Branch: `feat/create-text-style`

---

## 1. Install Bun

The fork builds with [Bun](https://bun.sh). Skip if `bun --version` already works.

```bash
curl -fsSL https://bun.sh/install | bash
bun --version
```

## 2. Clone the fork

```bash
git clone -b feat/create-text-style https://github.com/dickyudhandika/figma-mcp-bridge.git
cd figma-mcp-bridge
```

Remember the absolute path — every MCP config needs it:

```bash
pwd
# e.g. /Users/you/code/figma-mcp-bridge
```

## 3. Install root dependencies

```bash
bun install
```

## 4. Build the server

The server is what your agent talks to. It must be built before anything works.

```bash
cd server
bun install
bun run build
```

Output: `server/dist/index.js`. This is the exact file your MCP config points to.

## 5. Build the plugin

```bash
cd ../plugin
bun install
bun run build
```

Output: `plugin/dist/` plus the emitted `plugin/manifest.json`.

> **Rebuild rule.** `server/dist/` and `plugin/dist/` are build artifacts. Editing
> anything in `server/src/` or `plugin/src/` does nothing until you re-run the
> matching `bun run build`.

## 6. Import the plugin into Figma

1. Open the **Figma desktop app** (the browser build cannot import dev plugins).
2. Open any Figma file.
3. Go to **Plugins → Development → Import plugin from manifest…**
4. Select `plugin/manifest.json` inside your cloned fork.
5. Run it: **Plugins → Development → Figma MCP Bridge**.

Keep the plugin window open in every file you want the agent to see — the bridge
only knows about files where the plugin is running.

## 7. Add the MCP server to your agent

See `mcp-config-examples.md`. Point it at the **absolute** path to
`server/dist/index.js` from step 4, then restart your agent (a full restart, not
just a config reload, for most agents).

## 8. Verify

Follow `verify.md`. Do not start the workshop until `list_files` returns your file.

---

## Port notes (only if you run the stock bridge too)

The server defaults to port **1994**, and the plugin's WebSocket URL is **baked in
at plugin build time** (`VITE_FIGMA_BRIDGE_WS`, default `ws://localhost:1994/ws`).

Two things share that port and will fight if you run the stock npm bridge and this
fork at the same time: both read `FIGMA_BRIDGE_PORT`, both default to 1994, and
they join the same leader election. The loser becomes a follower with no plugin
attached — silent breakage.

If you must run both, give the fork a second port and rebuild the plugin for it:

```bash
# 1. server — pass FIGMA_BRIDGE_PORT=1995 in the MCP server's env
#    (see the env: example in mcp-config-examples.md)

# 2. plugin — rebuild with the matching WS URL
cd plugin
unset NODE_ENV
VITE_FIGMA_BRIDGE_WS=ws://localhost:1995/ws bun run build

# 3. manifest — the plugin may only open sockets to allowed domains
python3 - <<'PY'
import json, pathlib
p = pathlib.Path('manifest.json')
m = json.loads(p.read_text())
m['networkAccess']['allowedDomains'] = ['ws://localhost:1995']
p.write_text(json.dumps(m, indent=2) + '\n')
PY
```

Then re-import the plugin in Figma (step 6). **For the workshop, don't do this** —
close the stock bridge, use the default port 1994, change nothing. One build, one
port, no env vars.

## Troubleshooting

| Symptom | Fix |
| --- | --- |
| `bun: command not found` | Install Bun (step 1), then reopen your terminal. |
| Agent shows no `create_text_style` tool | You pointed MCP at the npm package instead of `server/dist/index.js`. Fix the path, restart. |
| `list_files` returns empty | The plugin isn't running. Open the file in Figma, run it via Plugins → Development. |
| Port 1994 already in use | A stale server child is running. `lsof -i :1994`, kill it, restart your agent. |
| `server/dist/index.js` missing | You skipped `bun run build` in `server/`. |
