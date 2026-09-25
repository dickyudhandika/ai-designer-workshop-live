# Phase 1 — Competitor Research (Mobile)

Agent prompt. **10 minutes**, hard time-boxed. Read `session-1/report-template.md` first — it defines
the fields *and* the Figma layout you must render. Both are fixed. Your job is to fill them, not to
design them.

**This phase researches mobile, from app screens.** Every capture is a phone-shaped app screen at
Mobbin's native **1179×2676**. Desktop screenshots and live browser captures are both out of scope
here — the homepage this workshop builds is a mobile marketplace homepage, so the evidence must be
mobile evidence.

---

## What is being built vs. what is being studied

These are two different things, and conflating them is the mistake this phase exists to avoid.

| | |
|---|---|
| **The use case (what Session 1 builds)** | A **photo marketplace app** — a mobile homepage where people browse and buy photographs. |
| **The references (what this phase studies)** | **Image-grid marketplace apps** — real apps whose home screen is a browseable grid of photographs. |

Stock-photography apps barely exist on Mobbin: of the ten obvious photo-marketplace brands
(Shutterstock, Getty, Unsplash, Pexels, Adobe Stock, iStock, EyeEm, Alamy, Depositphotos,
Dreamstime), **one** has app screens worth using. Researching that list returns a nearly empty page.

So study the apps that already solved the *design problem* the photo marketplace has: **a mobile
home page whose entire job is to show a grid of photographs and let you search it.** Depop, Etsy and
Vinted have solved a harder version of that problem — their grids carry price, brand, size and
condition on top of the image. Inherit from them; build the photo marketplace.

**Never invent a competitor, a screen, or a metric.** Every claim carries a URL.

---

## Time budget

This phase has blown past 10 minutes before, almost entirely on layout tinkering and prose padding.
The budget below is the fix. Track it. If a step overruns, cut scope — never extend the clock.

| Step | Budget | What overruns, and why |
|---|---|---|
| Query + download screens | 4 min | Chasing a category that Mobbin doesn't cover. Probe first, commit once. |
| Write the report | 3 min | Writing long paragraphs instead of 7 capped fields. |
| Render the Figma page | 3 min | Rebuilding the layout from scratch. The contract is pre-decided — follow it. |
| Verify | 1 min | Per-screen vision checks. Do **one** check, of the whole page. |

**Rule of thumb:** if you are more than 2 minutes into the Figma step and still deciding spacing or
frame structure, stop and re-read the render contract in `report-template.md`. Every number is there.

---

## Goal

Find 5 real **image-grid marketplace apps** with usable home screens. Extract the 7 observation fields
from `report-template.md`. Synthesize cross-app patterns. Recommend **one** as the Phase 3 design
reference for the photo marketplace homepage. Render the same research as a `Research` page in Figma
with a real app screen per reference.

Research once. Render twice. Never re-research to fill a Figma frame.

---

## The source — Mobbin MCP

Mobbin is the source. It exposes exactly three tools:

| Tool | Use it for |
|---|---|
| `search_screens` | Individual UI screens — **this is the one Phase 1 runs on** |
| `search_flows` | Multi-step flows (onboarding, checkout). Skip unless you need a flow. |
| `search_sections` | Website sections (About, Pricing). Not relevant to an app homepage. |

`search_screens` params: `query` (plain language, one screen at a time), `platform` (`ios` / `web`),
`mode` (`standard` for speed, `deep` for AI-scored relevance), `limit`, `image_format`.

Two rules that decide whether a query works:

- **Describe one screen in plain language**, not a keyword list. `"marketplace app home screen with
  photo grid and search bar"` works. `"photo marketplace stock"` returns nothing.
- **Never put the platform inside the query.** `platform` is a separate parameter. `"photo app ios"`
  degrades the match.

### The probe that works

Start here — it returns image-grid marketplaces, which is exactly the reference set this phase wants:

```
search_screens("marketplace app home screen with photo grid and search bar",
               platform="ios", limit=12)
```

That query reliably returns: Depop, Vestiaire Collective, Faire Wholesale, Nextdoor, eBay, Etsy,
Instacart, Urban Company, Artsy, OpenSea, Amazon Shopping, Careem.

Named-company queries also work: `"Depop home screen"`, `"Vinted home feed"`, `"Etsy home screen"`.

### Rule: empty result → drop the candidate

If a query returns `[]`, **try at most two variations, then drop the candidate.** Do not retry a dead
query — it is dead, and each retry costs a minute you don't have. Say in chat which candidates you
dropped and why.

---

## The worked example — 5 references, verified

This is a completed probe, run against real Mobbin data. Use it as the starting set, or run your own
probe and replace it.

| # | App | Home screen shows | Search field | Grid |
|---|---|---|---|---|
| 1 | **Depop** | Greeting, full-width search, 2-column grid | ✅ | 2-col, 6 tiles |
| 2 | **Vinted** | Category tabs, "Recommended for you" | ✅ | 2-col, 4 tiles |
| 3 | **Vestiaire Collective** | "Now Trending" carousel bands | ✅ | carousels |
| 4 | **Etsy** | Search, category tiles, curated rows | ✅ | mixed |
| 5 | **Nextdoor** | Filter chips above a listings grid | ✅ | 2-col, 6 tiles |

Five distinct products, all with a photo-led home screen and a search input. Nothing is padded with a
near-duplicate.

**Coverage note for the audience:** this is the honest finding — the photo *category* is nearly absent
from Mobbin, the image-grid *pattern* is everywhere. Say so rather than forcing the category.

---

## Why these five and not the photo brands

Requirement for a usable reference: a **home screen** (not a search-results or detail screen) that is
**photo-led** (a grid or carousel of images) and carries a **search input** — so Session 2 has real
placeholders to fill and Phase 3 has real structural decisions to inherit.

Checked against real data:

| Category | Coverage on Mobbin | Verdict |
|---|---|---|
| **Image-grid marketplaces** | 12+ apps, home screens with grids | ✅ **used** |
| Fashion resale | 10+ | ✅ strong |
| Real estate / stays | 12+ | ⚠️ runner-up — only 1 of 6 sampled screens was a home screen |
| Art / NFT | 6 | ⚠️ NFT noise |
| Home & interior | 4 | ❌ shop tab, not home screen |
| Recipes | 6 | ❌ 4 of 6 had back arrows — not home screens |
| Design inspiration | Behance, VSCO, Google Arts | ❌ **zero search fields** |
| Print-on-demand | **1** (Redbubble) | ❌ coverage fail — 1 company cannot fill 5 slots |
| Stock photo brands | **1** (Unsplash) | ❌ coverage fail |

---

## Capture — app screens, not browser captures

**You are not running a browser in this phase.** Mobbin returns app screens directly, already
phone-shaped, already the right ratio. There is no capture pass, no bot-block to route around, no
viewport to configure.

- Download each screen to `output/research/screens/<slug>.png` — lowercase, hyphens (`vinted`,
  `vestiaire-collective`). Create the directory first; it may not exist yet.
- **Pick the home screen, not the first result.** `search_screens` returns several screens per app.
  Look at them and choose the one whose home tab is active and whose grid is visible. Grabbing
  result 0 blindly is how a search-results page ends up captioned as a home screen.
- Downscale to ~360px wide before embedding into Figma (see the render contract).

**No vision pass per screen.** You identify the home screen while choosing it — that is the evidence.
Vision is for **one** end-of-phase check of the finished Figma page.

**Mobbin down, or a candidate returns `[]` after two variations?** Draw the wireframe from your
recorded `Layout` field in the same slot and label it `wireframe — capture unavailable`. Say so in
chat. Never leave an unexplained empty frame, and never fake an image.

---

## Extraction — 7 observation fields

Use exactly the fields and caps in `session-1/report-template.md`. Summary:

| Field | Cap |
|---|---|
| URL | — |
| Capture | — (`app screen` / `wireframe`) |
| Layout | ≤180 chars |
| Nav & search | ≤180 chars |
| Grid | ≤120 chars |
| Primary action | ≤120 chars |
| Mobile pattern | ≤200 chars |
| Works | ≤120 chars |
| Weak | ≤120 chars |
| Notes *(optional)* | ≤120 chars |

**`Mobile pattern` is the field that earns this page.** It is the mobile-specific structural decision
worth inheriting. Not "has a nav bar": *"persistent bottom tab bar, 4 items, search collapsed to an
icon in the top bar"* or *"no bottom nav — search is the entire first screen"*. If the field could be
answered from the desktop site too, it is not a mobile pattern and does not belong in it.

Colour and typography are not fields. Phase 2 assigns them from `assets/DESIGN.md`, and a reference's
hex values don't transfer. Use `Notes` only if the reference does something *structurally* interesting
with them.

---

## Synthesis rules

- **A pattern in 3+ references is an industry standard.** Say so. Phase 3 inherits it.
- **A pattern only 1–2 do well is a differentiator.** Flag it as an opportunity.
- **A repeated weakness is an opportunity.** If three apps bury search, that's a deliberate decision
  worth making differently.
- 3–6 bullets, each ≤180 chars, grouped under `**Industry standards**` and `**Differentiators**`
  headings with a closing opportunity line. A bullet needing two sentences is two bullets.
- Weigh the **mobile** consequence of each bullet. "Search is the primary object" means something
  different at 390px wide than at 1440 — say what it means for the phone.

---

## Output — two passes, same research

### Pass 1 — report to disk (3 min)

Write `output/research/competitor-analysis.md` in the structure of `session-1/report-template.md`.
Do not rename, reorder, or drop sections. Respect the caps.

End with a **Recommendation**: one reference, named, ≤3 sentences grounded in the research above.

**Do this before touching Figma.** The markdown is the checkpoint — if a render call fails you lose
a frame, not the research.

### Pass 2 — render it into Figma (3 min)

**Open `session-1/report-template.md` and follow the "Render contract" section literally.** It
specifies the full node tree, the portrait slot size, the accent-panel construction, fills, strokes,
spacing, and the layout mechanics that previously cost a rebuild each.

Your job here is transcription, not layout design. Specifically:

1. `create_page` → `Research`. Reuse the page if it already exists; don't accumulate duplicates.
2. Build `Research — Image-Grid Marketplace Home Screens` (root frame, width **1224**, height **HUG**)
   and the Header.
3. Build the wrapping `Rows` container (**1128** wide, fixed), then one **360**-wide card per
   reference in document order — **3 per row**, wrapping to 2.
4. Place each app screen in its **312×708** portrait slot. Images need **absolute** paths — relative
   paths resolve against the MCP server's own working directory, not this repo. If the bridge refuses
   the path, stage the file inside the server's working directory and copy it to `output/` after, and
   say so.
5. `Cross-App Patterns`, `Recommendation`, `Chosen` — same spec, `Recommendation` and `Chosen` get the
   accent panel treatment.

Then `save_screenshots` on the `Research` page → `output/figma/research-page.png` (absolute path).
If the tool writes elsewhere, copy it into place and say so. **Delete the target file first** —
`save_screenshots` silently refuses to overwrite and you will keep the previous build's PNG.

**Verify once, at the end:** look at the finished page as a whole. Check the vertical order, that
every card shows a real app screen, and that nothing is clipped or empty. One check. Not five.

---

## MCP / tools used

- Mobbin MCP `search_screens` — the reference set (Path A, the only path)
- `create_page`, `create_frame`, `create_text`, `create_image`, `set_solid_fill`, `set_auto_layout`,
  `set_stroke_properties`, `save_screenshots` — the Figma render
- `write_file` — the markdown artifact

---

## Then: PAUSE

Present three things: the report summary (who was studied, the cross-app pattern, your
recommendation), the `Research` page screenshot, and an invitation to look at the room's own Figma
window.

**Stop. Let the human pick the reference.** They may override your recommendation — that's their call.

Once they pick, record it in **both** artifacts before Phase 2:

1. Append the `**Chosen:**` line under the Recommendation in `output/research/competitor-analysis.md`
2. Replace the `Chosen` frame's placeholder with `Chosen: <pick>`, keeping the accent panel so the
   confirmed pick reads the same as the recommendation

---

## Done when

- `output/research/competitor-analysis.md` exists, capped fields, 5 references
- Each reference has a URL and a `Capture:` value (`app screen` or `wireframe`)
- Cross-App Patterns lists 3–6 bullets, each weighing the mobile consequence
- Recommendation names exactly one reference
- `Research` page in Figma: 5 cards in document order + `Cross-App Patterns` + `Recommendation` + `Chosen`
- `output/figma/research-page.png` exists
- Every card carries a real app screen or a wireframe labelled `wireframe — capture unavailable`
- Any candidate dropped for an empty Mobbin result is named in chat — no silent gaps
- The human's choice is on record in both artifacts

---

## If Mobbin is unavailable

Degrade, don't stall. In order:

1. **Mobbin returns `[]` for everything** (auth expired, or the service is down) → write the markdown
   from whatever you can verify, and for every slot you cannot fill draw a wireframe in the same
   312×708 slot labelled `wireframe — capture unavailable`. State plainly in chat and at the top of the
   report: `Mobbin unavailable — screens are wireframes.` Never pad with near-duplicates and never
   describe a screen from memory.
2. **Mobbin is fine but the Figma bridge is down** → write the markdown report normally, skip Pass 2,
   and state: `Figma render skipped — bridge unavailable.`

Either way, do not fake frames and do not emit a substitute HTML page. Continue to Phase 2, which has
its own documented degradation path. One dead service never stops the session.
