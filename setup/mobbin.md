# Mobbin MCP

Session 1 step 2 researches real mobile screens on Mobbin. This is the setup.

**Mobbin is the one dependency you cannot work around.** It's a paid product, it's remote, and if it isn't connected step 2 returns `[]` for every query with no error. Test it before the workshop, not during it.

---

## What it is

Not a local server. There is **nothing to clone, install, or build**, and **no API key**.

Mobbin runs a hosted remote MCP server at:

```text
https://api.mobbin.com/mcp
```

Transport is **Streamable HTTP**, auth is **OAuth**. On first use your agent opens a browser window, you sign in to Mobbin, and you authorize access. That's the whole setup.

Source: [github.com/mobbin/mobbin-mcp-server](https://github.com/mobbin/mobbin-mcp-server) · [docs.mobbin.com/mcp](https://docs.mobbin.com/mcp)

---

## 1. You need a paid Mobbin plan

**Mobbin MCP is available on Pro and Team plans. It is not on the free plan.**

This is the trap worth knowing in advance. A free Mobbin account can add the server, complete the OAuth flow, and look connected — and every query still comes back empty. Nothing in the error will tell you it's a billing problem.

Check your plan before the session: [mobbin.com/pricing](https://mobbin.com/pricing)

**Mobbin MCP requires a paid plan, and that's the intended path.** Sort this out before the session — a free account connects, completes OAuth, looks fine, and then returns `[]` for every query with no error. There is no working substitute for what Mobbin gives the room: real shipped screens at phone resolution. Buy the plan.

**Usage during beta is unlimited.** Mobbin says limits will apply later ([docs.mobbin.com/ai-credits](https://docs.mobbin.com/ai-credits)) — so don't ration queries in the session. The library is 600,000+ shipped screens.

---

## 2. Add the server

One line of config, and it's the same for every client — unlike the Figma bridge, there's no local path to get right.

```json
{
  "mcpServers": {
    "mobbin": {
      "url": "https://api.mobbin.com/mcp"
    }
  }
}
```

Per-client file locations are in `mcp-config-examples.md`.

**Cline is the exception.** It needs the transport stated explicitly, or it falls back to the legacy SSE transport and the connection fails:

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

**Hermes** uses YAML, and marks the auth mode:

```yaml
mcp_servers:
  mobbin:
    url: https://api.mobbin.com/mcp
    auth: oauth
```

**Some clients have one-click install** — Claude Code, Cursor, Codex, ChatGPT, Figma, v0 among them. See [docs.mobbin.com/mcp/clients/overview](https://docs.mobbin.com/mcp/clients/overview). If your agent is on that list, use it and skip the config block.

Then **fully restart the agent.** Most agents only read MCP config at startup.

---

## 3. Authorize

First use triggers the OAuth flow. A browser window opens, you sign in to your Mobbin account, and you approve access.

Two things that go wrong here:

- **The window opens behind your terminal or editor.** If nothing seems to happen, look for it before assuming it failed.
- **You need to be signed in to the right Mobbin account** — the one with the paid plan.

In a live workshop, do this **before** the room is watching. It's a browser round-trip, and it interrupts the flow.

---

## What your agent gets

Three search tools:

| Tool | What it searches |
|---|---|
| `search_screens` | UI screens — a single screen in an app |
| `search_flows` | Multi-step flows — onboarding, checkout |
| `search_sections` | Website sections — pricing pages, footers |

Session 1 uses `search_screens` almost exclusively, because it's researching home screen layouts one screen at a time.

**Results carry two images:** a low-res preview the agent reads, and a high-res `image_url` it downloads when saving or exporting. **`image_url` expires after 30 days** — if you're capturing screens for a deck or a report, download them when you find them, not later.

Source: [docs.mobbin.com/mcp/features](https://docs.mobbin.com/mcp/features)

---

## Verify it

Don't skip this. Mobbin fails silently in a way the Figma bridge doesn't — there's no process to check with `lsof`, and a disconnected server looks exactly like a search that found nothing.

**Check 1 — the tools are registered.** Ask your agent to list its MCP tools. Expected: `search_screens`, `search_flows`, `search_sections`.

Missing → the config isn't being read. Check the file location for your client in `mcp-config-examples.md`, then restart the agent.

**Check 2 — a real query returns real results.** This is the one that matters:

> Search Mobbin for onboarding screens from banking apps. Tell me how many came back and name three of the apps.

Expected: a number in the dozens and three real app names. **Not** an empty array, and **not** an answer written from memory.

**Empty result?** In order of likelihood:

1. **Free Mobbin plan.** The most common cause, and the least obvious. Check your plan.
2. **OAuth never completed.** The server is added but not authorized. Re-run a query and watch for the browser window.
3. **Query shaped wrong.** Session 1 step 2 documents the three rules that make a query return anything — one screen described in plain language, platform kept out of the text, one screen at a time. A keyword pile like `"photo marketplace stock"` returns `[]` even on a paid plan with a working connection.
4. **Agent restarted before the config was saved.**

Full session-level detail on query shape: `session-1.md` step 2.
