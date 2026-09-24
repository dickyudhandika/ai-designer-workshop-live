# MCP Config Examples

Add the figma-bridge MCP server to whichever agent you use. All examples point at
the **fork's locally built server** — not the npm package, because the npm package
lacks the token-authoring tools this workshop needs.

**Replace `/absolute/path/to/figma-mcp-bridge` everywhere below** with the path
you cloned the fork to. Verify the file exists first:

```bash
ls /absolute/path/to/figma-mcp-bridge/server/dist/index.js
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
      "args": ["/absolute/path/to/figma-mcp-bridge/server/dist/index.js"]
    }
  }
}
```

Quit Claude Desktop completely and reopen it.

## Claude Code (CLI)

File: `.mcp.json` in your project root (project scope), or run
`claude mcp add figma-bridge -- node /absolute/path/to/figma-mcp-bridge/server/dist/index.js`

```json
{
  "mcpServers": {
    "figma-bridge": {
      "command": "node",
      "args": ["/absolute/path/to/figma-mcp-bridge/server/dist/index.js"]
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
      "args": ["/absolute/path/to/figma-mcp-bridge/server/dist/index.js"]
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
      "args": ["/absolute/path/to/figma-mcp-bridge/server/dist/index.js"]
    }
  }
}
```

## Codex (OpenAI)

File: `~/.codex/config.toml`

```toml
[mcp_servers.figma-bridge]
command = "node"
args = ["/absolute/path/to/figma-mcp-bridge/server/dist/index.js"]
```

## VS Code / Copilot Chat

File: `.vscode/mcp.json` in your project root.

```json
{
  "servers": {
    "figma-bridge": {
      "type": "stdio",
      "command": "node",
      "args": ["/absolute/path/to/figma-mcp-bridge/server/dist/index.js"]
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
      - /absolute/path/to/figma-mcp-bridge/server/dist/index.js
    enabled: true
```

---

## Optional: overriding the port

Only needed if a stock npm bridge is also running on the default port 1994 (see the
port notes in `install-figma-bridge.md`). Add an env map to the server entry:

```json
{
  "mcpServers": {
    "figma-bridge": {
      "command": "node",
      "args": ["/absolute/path/to/figma-mcp-bridge/server/dist/index.js"],
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
      - /absolute/path/to/figma-mcp-bridge/server/dist/index.js
    env:
      FIGMA_BRIDGE_PORT: "1995"
    enabled: true
```

The plugin must be rebuilt with the matching `VITE_FIGMA_BRIDGE_WS` and have its
manifest `allowedDomains` updated, or it will connect nowhere.

---

## Confirm it worked

Ask your agent to call `list_files`. You should see the tools listed in
`install-figma-bridge.md`, and `create_text_style` / `create_variable_collection`
must be present — if they're missing, you're talking to the npm package, not the
fork. Then continue to `verify.md`.
