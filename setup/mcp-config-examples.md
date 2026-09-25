# MCP Config Examples

Two MCP servers, two very different setups:

- **`figma-bridge`** — a local process you build and point at a path. Config differs per client.
- **`mobbin`** — a hosted remote server. **Nothing to build, no API key.** The config is the same line everywhere.

Add both to whichever agent you use, then restart it.

---

# figma-bridge

All examples point at the **fork's locally built server** — not the npm package, because the npm package lacks the token-authoring tools this workshop needs.

**Clone the fork to `~/Downloads/figma-mcp-bridge` and build it first** — see
`install-figma-bridge.md`. Every config below points at that build, because the npm
package lacks the token-authoring tools this workshop needs.

Replace `/Users/<you>` with your actual home directory. Verify the file exists first:

```bash
ls ~/Downloads/figma-mcp-bridge/server/dist/index.js
```

If that errors, build the fork — see `install-figma-bridge.md`.

After editing config, **restart your agent.** Most agents only read MCP config at
startup; a settings reload is often not enough.

---

## Claude Desktop

File: `~/Library/Application Support/Claude/claude_desktop_config.json` (macOS)
File: `%APPDATA%\Claude\claude_desktop_config.json` (Windows)

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

Quit Claude Desktop completely and reopen it.

## Claude Code (CLI)

File: `.mcp.json` in your project root (project scope), or run
`claude mcp add figma-bridge -- node /Users/<you>/Downloads/figma-mcp-bridge/server/dist/index.js`

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

## Cursor

File: `.cursor/mcp.json` in your project root (project scope) or
`~/.cursor/mcp.json` (global).

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

Then: Cursor Settings → MCP → confirm `figma-bridge` shows as connected / green.

## Windsurf

File: `~/.codeium/windsurf/mcp_config.json`

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

## Codex (OpenAI)

File: `~/.codex/config.toml`

```toml
[mcp_servers.figma-bridge]
command = "node"
args = ["/Users/<you>/Downloads/figma-mcp-bridge/server/dist/index.js"]
```

## VS Code / Copilot Chat

File: `.vscode/mcp.json` in your project root.

```json
{
  "servers": {
    "figma-bridge": {
      "type": "stdio",
      "command": "node",
      "args": ["/Users/<you>/Downloads/figma-mcp-bridge/server/dist/index.js"]
    }
  }
}
```

## Hermes

File: `~/.hermes/config.yaml`

```yaml
mcp_servers:
  figma-bridge:
    command: node
    args:
      - /Users/<you>/Downloads/figma-mcp-bridge/server/dist/index.js
    enabled: true
```

---

# mobbin

Remote, hosted, no build. One URL for every client.

```json
{
  "mcpServers": {
    "mobbin": {
      "url": "https://api.mobbin.com/mcp"
    }
  }
}
```

Add it alongside `figma-bridge` inside the same `mcpServers` object — don't replace it. Per-client file locations are the same as the figma-bridge section above, with two exceptions:

**Claude Desktop / Claude Code / Cursor / Windsurf / VS Code** — same file as figma-bridge, same `mcpServers` key. Both servers sit side by side:

```json
{
  "mcpServers": {
    "figma-bridge": {
      "command": "node",
      "args": ["/Users/<you>/Downloads/figma-mcp-bridge/server/dist/index.js"]
    },
    "mobbin": {
      "url": "https://api.mobbin.com/mcp"
    }
  }
}
```

**Codex** — TOML, so the shape differs:

```toml
[mcp_servers.figma-bridge]
command = "node"
args = ["/Users/<you>/Downloads/figma-mcp-bridge/server/dist/index.js"]

[mcp_servers.mobbin]
url = "https://api.mobbin.com/mcp"
```

**Hermes** — YAML, and it marks the auth mode:

```yaml
mcp_servers:
  figma-bridge:
    command: node
    args:
      - /Users/<you>/Downloads/figma-mcp-bridge/server/dist/index.js
    enabled: true
  mobbin:
    url: https://api.mobbin.com/mcp
    auth: oauth
```

**Cline needs the transport stated explicitly** or it falls back to the legacy SSE transport and fails:

```json
{
  "mcpServers": {
    "mobbin": {
      "type": "streamableHttp",
      "url": "https://api.mobbin.com/mcp"
    }
  }
}
```

**One-click install for some clients.** Claude Code, Cursor, Codex, ChatGPT, Figma and v0 have a guided install — see [docs.mobbin.com/mcp/clients/overview](https://docs.mobbin.com/mcp/clients/overview). Use it and skip the config above.

**First use opens a browser window** to sign in to Mobbin and authorize. That requires a **paid Pro or Team plan** — a free account connects and then returns nothing. Full detail, including the fallback if nobody in the room has a paid plan: `setup/mobbin.md`.

**Restart your agent** after adding it, same as the bridge.

---

# Optional: overriding the port

Only needed if a stock npm bridge is also running on the default port 1994 (see the
port notes in `install-figma-bridge.md`). Add an env map to the server entry:

```json
{
  "mcpServers": {
    "figma-bridge": {
      "command": "node",
      "args": ["/Users/<you>/Downloads/figma-mcp-bridge/server/dist/index.js"],
      "env": {
        "FIGMA_BRIDGE_PORT": "1995"
      }
    }
  }
}
```

```yaml
# Hermes
mcp_servers:
  figma-bridge:
    command: node
    args:
      - /Users/<you>/Downloads/figma-mcp-bridge/server/dist/index.js
    env:
      FIGMA_BRIDGE_PORT: "1995"
    enabled: true
```

The plugin must be rebuilt with the matching `VITE_FIGMA_BRIDGE_WS` and have its
manifest `allowedDomains` updated, or it will connect nowhere.

---

## Confirm it worked

**Mobbin:** ask your agent to list its MCP tools and confirm `search_screens`, `search_flows` and `search_sections` are there. Then run a real query — see step 1 of `verify.md`. An empty result on a working connection usually means a free Mobbin plan, not a bad config.

**figma-bridge:** ask your agent to call `list_files`. You should see the tools listed in
`install-figma-bridge.md`, and `create_text_style` / `create_variable_collection`
must be present — if they're missing, you're talking to the npm package, not the
fork. Then continue to `verify.md`.
