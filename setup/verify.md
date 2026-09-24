# Verify the Figma MCP Bridge

Run these four checks in order. Do not start Session 1 until all four pass — a
half-connected bridge fails silently and burns workshop time.

Have your agent run the MCP calls; run the shell commands yourself.

---

## 0. Prerequisite state

- Fork cloned and built (`server/dist/index.js` exists) — see `install-figma-bridge.md`
- MCP server added to your agent's config — see `mcp-config-examples.md`
- Agent restarted **after** the config edit
- Figma **desktop** app open, a file open, plugin running
  (**Plugins → Development → Figma MCP Bridge**)

---

## 1. Server process is alive

```bash
lsof -i :1994
```

Expected: a `node` process listening on port 1994 (TCP, LISTEN).

Nothing there? Your agent never spawned the server — usually a bad path in the MCP
config. Confirm `ls /absolute/path/to/figma-mcp-bridge/server/dist/index.js` works,
then restart the agent.

Running the fork on a different port? Check that port instead.

## 2. Tools are registered

Ask your agent to list its available MCP tools and confirm **all four** workshop
tools are present:

- `create_variable_collection`
- `create_variables`
- `set_bound_variable`
- `create_text_style`

Missing any of them means you pointed the config at the stock npm package instead
of the fork's `server/dist/index.js`. Fix the path and restart.

## 3. Agent sees the file

Call **`list_files`**. Expected: JSON array with `fileKey` and `fileName` for each
connected Figma file.

```json
[{ "fileKey": "unsaved-m1a2b3c-x7k2", "fileName": "Untitled" }]
```

Empty array → the plugin isn't running in any file. Open the file in Figma and run
it: **Plugins → Development → Figma MCP Bridge**. Keep the plugin window open.

`fileKey` starting with `unsaved-` is normal for a Figma file that has never been
saved to the cloud. Everything still works — reads, writes, variables, styles. Save
the file in Figma when convenient; the key changes and you re-run `list_files`.

Multiple files open? Pass that `fileKey` explicitly to every subsequent call so the
agent doesn't act on the wrong file.

## 4. Reads work

Call **`get_metadata`** with that `fileKey`. Expected: file name, the page list, and
the current page.

Then call **`get_styles`**. Expected: whatever local styles the file already has
(an empty-ish list on a fresh file is fine).

## 5. Writes work — the two that matter

Reading is upstream behaviour and almost always works. The fork's new tools are
what Session 1 Phase 2 depends on, so test them now.

### a. Frame (proves basic write)

Call `create_frame` with a small test frame, e.g. `{ "name": "verify-test", "width": 100, "height": 100, "fillHex": "#1A5EFF", "fileKey": "<your fileKey>" }`.

It must appear in Figma. Delete it when done.

### b. Variables (proves the fork)

1. `create_variable_collection` with `{ "name": "Verify", "fileKey": "<your fileKey>" }`
   → returns a `collectionId`.
2. `create_variables` with that `collectionId`:

```json
{
  "collectionId": "<collectionId>",
  "variables": [
    { "name": "color/test", "resolvedType": "COLOR", "value": "#1A5EFF" }
  ],
  "fileKey": "<your fileKey>"
}
```

→ returns a variable ID. Open Figma's **Local variables** panel; `Verify /
color/test` must be there.

Clean up with `delete_variable_collection` (deletes its variables too) before the
workshop.

### c. Text style (proves the trickier fork tool)

Call `create_text_style`. Note the exact parameter shapes — this tool takes
`fontStyle` as a **name string**, not a numeric weight, and `lineHeight` /
`letterSpacing` as `{value, unit}` objects:

```json
{
  "name": "Verify/Body",
  "fontFamily": "Inter",
  "fontStyle": "Regular",
  "fontSize": 16,
  "lineHeight": { "value": 150, "unit": "PERCENT" },
  "letterSpacing": { "value": 0, "unit": "PERCENT" },
  "fileKey": "<your fileKey>"
}
```

→ confirm `Verify/Body` appears in Figma's Local text styles.

Got `"Inter could not be loaded"`? Your Figma session lacks the font. Fix with
**Text → font menu → install/lookup**, or pick a family you do have. This is the
same failure mode Session 1 hits with `Fauna One` — that prompt documents the
`Playfair Display` fallback. Seeing it here is useful.

## 6. Screenshots land where expected

Call `save_screenshots` with the test frame's node ID. Note the `items` array shape:

```json
{
  "items": [{ "nodeId": "<test frame nodeId>", "outputPath": "/absolute/path/to/ai-designer-workshop-live/output/figma/verify.png", "format": "PNG", "scale": 2 }],
  "fileKey": "<your fileKey>"
}
```

**Use an absolute `outputPath`.** Relative paths resolve against the MCP server's
own working directory (the fork clone), not this repo. Then confirm the file exists:

```bash
ls -la output/figma/verify.png
```

---

## Troubleshooting

| Symptom | Cause | Fix |
| --- | --- | --- |
| Port 1994 not listening | Server never started | Bad config path or agent not restarted. See step 1. |
| Tools missing / no `create_text_style` | Talking to the npm package | Point config at the fork's `server/dist/index.js`. |
| `list_files` empty | Plugin not running | Open the file in Figma, Plugins → Development → Figma MCP Bridge. |
| Two builds, one dead plugin | Stock bridge and fork fighting over port 1994 | Close the stock bridge and keep default 1994. Otherwise see the port notes in `install-figma-bridge.md`. |
| Font load error | Font not in your Figma session | Pick an installed family, or use the documented fallback. |
| Screenshot at the wrong place | Relative `outputPath` | Pass an absolute path. |
| Writes fail after editing `server/src/` | `server/dist/` is stale | `cd server && bun run build`, then restart the agent. |

Once step 6 passes, you're ready: tell your agent to **read `AGENTS.md` and run the
workshop.**
