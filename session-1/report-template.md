# Image-Grid Marketplace Competitor Analysis

> **Fixed fields, hard caps, fixed Figma layout.** Fill it in. Do not add sections, do not reorder
> fields, do not invent a different visual treatment — the layout below is pre-decided so nobody
> spends the session rebuilding it.
>
> **The use case is a photo marketplace app. The references are image-grid marketplace apps.** Stock
> photo apps barely exist on Mobbin; image-grid marketplaces are everywhere. Study the apps that
> already solved "a mobile homepage that shows a grid of photographs you can search" — then build the
> photo marketplace on those decisions. See `phase-1-research.md`.
>
> **App screens only.** Every capture is an app screen at Mobbin's native **1179×2676**. No browser,
> no viewport config, no desktop pages — this page is evidence for building a mobile marketplace
> homepage.
>
> **Budget:** query + download ≤4 min · report ≤3 min · Figma render ≤3 min · verify ≤1 min.
> Past budget means you are over-writing. Cut prose, never competitors.
>
> **This file drives both Phase 1 artifacts:** `output/research/competitor-analysis.md`, and the
> `Research` page in Figma that mirrors it. Research once, render twice. See `phase-1-research.md`.

---

## Field set — 7 observation fields, hard caps

Plus two metadata fields (`URL`, `Capture`) and one optional (`Notes`). Ten lines per competitor —
nine when `Notes` is omitted.

The caps are the point. A field that runs long is a field that was padded. If it doesn't fit,
the observation isn't specific enough yet.

| Field | What to record | Cap |
|---|---|---|
| **URL** | Exact product URL. No prose. | — |
| **Capture** | `app screen` or `wireframe` — what the audience is actually looking at | — |
| **Layout** | Section order top→bottom, where the first screen cuts, how much chrome before the first photo | ≤180 chars |
| **Nav & search** | Nav pattern (top bar / bottom tabs / drawer) + items + search prominence (high/med/low) and where it sits | ≤180 chars |
| **Grid** | Masonry / uniform / columns at mobile width, density, gutters | ≤120 chars |
| **Primary action** | The one most important control — its label and where it sits | ≤120 chars |
| **Mobile pattern** | The mobile-specific structural decision worth inheriting — thumb reach, one-hand affordances, what collapsed and what stayed | ≤200 chars |
| **Works** | One specific thing done well | ≤120 chars |
| **Weak** | One specific failure | ≤120 chars |
| **Notes** | *Optional.* Colour, typography, image sourcing — **only if it changes a Phase 3 decision** | ≤120 chars |

**`Mobile pattern` is the field that earns this page, and it gets the widest cap (200).** It must say
something a desktop-only review could not: *"bottom tab bar, 4 items, search collapsed to a top-bar
icon"*, *"no bottom nav — search owns the entire first screen"*, *"filters live behind a sheet, never a
persistent rail"*. If the observation would be equally true at 1440px, it is not a mobile pattern —
put it in `Nav & search`.

Colour and typography are deliberately not first-class fields: Phase 2 assigns those from
`assets/DESIGN.md`, and a reference's hex values don't transfer. Promote them into `Notes` only when
the reference does something *structurally* interesting with them.

**One more thing this field set must carry:** since the references are not photo marketplaces, every
card has to make the *transfer* explicit. State what the reference proves about a photo grid — its
search prominence, its tile density, its bottom-bar behaviour — not just what it does for resale or
local listings.

---

## Competitors Found

### 1. [Name] — [market position]
- URL: [link]
- Capture: [app screen / wireframe]
- Layout: [≤180 chars]
- Nav & search: [≤180 chars]
- Grid: [≤120 chars]
- Primary action: [≤120 chars]
- Mobile pattern: [≤200 chars — the field that earns the page]
- Works: [≤120 chars]
- Weak: [≤120 chars]
- Notes: [≤120 chars, optional — delete the line if nothing qualifies]

### 2. [Name] — [market position]
- URL: [link]
- Capture: [source]
- Layout: [≤180 chars]
- Nav & search: [≤180 chars]
- Grid: [≤120 chars]
- Primary action: [≤120 chars]
- Mobile pattern: [≤200 chars — the field that earns the page]
- Works: [≤120 chars]
- Weak: [≤120 chars]
- Notes: [optional]

### 3. [Name] — [market position]
- URL: [link]
- Capture: [source]
- Layout: [≤180 chars]
- Nav & search: [≤180 chars]
- Grid: [≤120 chars]
- Primary action: [≤120 chars]
- Mobile pattern: [≤200 chars — the field that earns the page]
- Works: [≤120 chars]
- Weak: [≤120 chars]
- Notes: [optional]

### 4. [Name] — [market position]
- URL: [link]
- Capture: [source]
- Layout: [≤180 chars]
- Nav & search: [≤180 chars]
- Grid: [≤120 chars]
- Primary action: [≤120 chars]
- Mobile pattern: [≤200 chars — the field that earns the page]
- Works: [≤120 chars]
- Weak: [≤120 chars]
- Notes: [optional]

### 5. [Name] — [market position]
- URL: [link]
- Capture: [source]
- Layout: [≤180 chars]
- Nav & search: [≤180 chars]
- Grid: [≤120 chars]
- Primary action: [≤120 chars]
- Mobile pattern: [≤200 chars — the field that earns the page]
- Works: [≤120 chars]
- Weak: [≤120 chars]
- Notes: [optional]

---

## Cross-App Patterns

**3–6 bullets. Each ≤180 chars.** A bullet that needs two sentences is two bullets. Each should weigh
the **mobile** consequence — "search is primary" means something different at 390px than at 1440.

- [Pattern in 3+ references = industry standard]
- [Pattern only 1–2 do well = differentiator]
- [Repeated weakness = opportunity]

---

## Recommendation

**Pick:** [one reference name]

**Why:** [≤3 sentences, grounded in the research above — not in taste]

**Chosen:** [human's final pick — may differ from the recommendation. Record here before Phase 2.]

---

# Render contract

The `Research` page in Figma is **not a design exercise** — it is a fixed layout that this data
flows into. Render it literally. Every number below is decided; do not recompute, restyle, or
"improve" spacing. That is where the previous 30-minute runs went.

**Portrait, because the evidence is app screens.** Cards are **360** wide and the screenshot slot is
**312×708**. The rows container narrows to match, so three portrait cards fit per row — five cards
land 3 + 2.

**Node tree, in document order:**

```
Research (page)
└── Research — Image-Grid Marketplace Home Screens   ← root frame, width 1224 (= 1128 + 2×48 pad), height HUG, pad 48, gap 32
    ├── Header                          ← vertical, gap 8, width 1128 FIXED
    │   ├── "Image-Grid Marketplace Home Screens"   44px Playfair Display 500  #1A1A1A
    │   └── "5 apps · iOS · Mobbin · YYYY-MM-DD · slot 312x708 (native 1:2.270)"   13px Inter 400  #8C8C8C
    ├── Rows                            ← horizontal, WRAP on, gap 24, width 1128 (3×360 + 2×24), FIXED
    │   └── Card "0N — Name" ×5         ← vertical, width 360, height HUG, pad 24, gap 16
    │       ├── "01 — Depop"           20px Inter Semi Bold  #1A1A1A
    │       ├── tag                    ← "Home feed — greeting, full-width search, 2-column grid"  12px Inter  #8C8C8C
    │       ├── Screenshot slot        ← frame 312×708 (portrait), fill #F2F1EC
    │       ├── fields                 ← one text node per field, "FIELDNAME ⏎ value", in template order, 13px Inter
    │       └── Accent panel           ← works + weak, see below
    ├── Cross-App Patterns              ← vertical, pad 24, gap 12, width 1128 FIXED
    │   ├── "Cross-App Patterns"   24px Playfair Display 500
    │   └── bullets                 ← heading node + ONE NODE PER BULLET, 13px Inter
    ├── Recommendation                  ← accent panel, width 1128
    └── Chosen                          ← accent panel, width 1128
```

**Geometry, stated once so it is never re-derived:**

| Value | Number |
|---|---|
| Root frame | **1224** wide · HUG tall · pad 48 · gap 32 |
| Rows container | **1128** wide (**FIXED**) · gap 24 · WRAP on |
| Card | **360** wide · HUG tall · pad 24 · gap 16 |
| Card inner width (text) | **312** |
| Screenshot slot | **312 × 708** — portrait, Mobbin native 1:2.270 |
| Cards per row | **3**, wrapping to 2 on row two |
| Accent bar | **2px** |

**Accent panel** — used once inside each card (works + weak), and for `Recommendation` and `Chosen`:

| Part | Spec |
|---|---|
| Panel | horizontal auto-layout, gap 0, width 1128 (or 312 in-card), height HUG, pad 0, radius 0 |
| Bar | frame, width **2px**, height = the content's real height, fill `#1A5EFF` |
| Content | vertical auto-layout, gap 8, width FILL, height HUG, pad 24 |

If a build can't stretch the bar, give it a fixed height matching the content block — **never**
switch to a full 1px box outline, and never emulate it with a stroke: this bridge only supports
uniform strokes, so a "left edge" stroke becomes a box around the whole thing. Read the content's
height from `bounds.height` on `get_node` — the bridge does **not** report `absoluteBoundingBox`, and
reading that key returns `None` silently, leaving the bar at its 100px default.

**Fill and stroke:**

| Element | Value |
|---|---|
| Page / root frame | `#FDFCF8` |
| Card | `#FFFFFF` with 1px `#E5E2D9` stroke, INSIDE |
| Image slot / placeholder | `#F2F1EC` |
| Competitor name | `#1A1A1A` 20px |
| Field text | `#1A1A1A` 13px |
| Tag / meta / wireframe label | `#8C8C8C` 12px |
| Accent bar | `#1A5EFF` 2px |
| Radius | `0px` everywhere |
| Spacing | 4px scale only: 4, 8, 12, 16, 24, 32, 48, 64 |

Phase 1 runs **before** Phase 2 creates the variables, so raw hex is correct on this page — use the
values above from `assets/DESIGN.md` and narrate that Phase 2 turns them into tokens.

**Layout mechanics that matter** (learned the hard way — skipping these costs a rebuild each):

- **Nested auto-layout throughout. No absolute coordinates.** Absolute positioning fights auto-layout
  and yields 100px-tall frames with 1600px children.
- **`primaryAxisSizingMode` controls a different axis per direction — this is the #1 silent failure.**
  On a **VERTICAL** frame the primary axis is **height**, so `primary="FIXED"` freezes the card at the
  100px default while its children stack far past it: the card looks empty and every child hangs
  outside its frame. On a VERTICAL container use **`primary="AUTO"` (hug height) + `counter="FIXED"`
  (pin width)**. On a **HORIZONTAL/WRAP** container it inverts: **`primary="FIXED"`** (pin width, which
  is what forces the wrap) **+ `counter="AUTO"`** (hug height).
- **A wrapping row must be width-FIXED.** The counter-intuitive one: a wrapping container set to hug
  its width never wraps — nothing constrains it, so all five cards stretch into one long line. Fix the
  `Rows` width to **1128** and the wrap happens.
- **Cards per row** — the count follows from 1128 and 360: **3 per row**, 2 on the second. Do not widen
  the cards to force a bigger number on row one; the portrait slot needs the height, and a landscape
  proportion would break the one-ratio rule that makes the row read as evidence.
- **Wrapped rows do NOT stretch children to a common height.** Cards come back ragged (e.g. 1484 /
  1421 / 1453 / 1437) and row two misaligns. After building all five, measure each card and set every
  card to the tallest — a final levelling pass, not a per-card fix inside the loop.
- **`create_image` needs an absolute path OR base64.** Relative paths resolve against the MCP server's
  own working directory. On a raw `/rpc` call the tool handler is bypassed entirely, so `source` is
  **not** resolved — pass `imageBase64` yourself. Downscale captures before embedding (~360px wide is
  plenty for a 312px slot) or the payload gets slow.
- **Node ids go at transport level, not inside `items`/`params`.** On a raw `/rpc` call the leader
  rebuilds `nodeId` from a top-level `nodeIds` array, so a `nodeId` left inside the params object is
  silently dropped and the tool fails with "No nodes to export" or "Required". *(Exception:
  `save_screenshots` takes an `items` array of `{nodeId, outputPath}` and is not node-targeting — its
  ids belong inside `items`.)*
- **There is no `delete_page` and no page rename.** `delete_nodes` refuses page nodes outright. So a
  failed build cannot clean up the page it created — pass a `TARGET_PAGE_ID` and reuse the page,
  deleting its children with `delete_nodes {confirm: true}` before rebuilding. Otherwise every retry
  leaves another stray empty page in the file.
- **Delete the screenshot path before exporting, every time.** `save_screenshots` refuses to overwrite
  and reports that in its *result*, not as an error — the call returns HTTP 200 with `total: 1` while
  `succeeded: 0` and `"File already exists at outputPath"`. Skip this and you keep the **previous**
  build's PNG on disk while believing you captured the new one; every downstream check then validates
  a stale image. Check `succeeded == 1` and confirm the file's mtime actually moved.
- **`save_screenshots` needs `format: "PNG"` uppercase**, and it only writes inside the MCP server's
  working directory (`~/.hermes` by default). Stage there, then copy to `output/figma/`.

---

## Screenshot rules

- **One ratio, one source — and it is portrait.** Mobbin app screens at their native **1179×2676**
  (measured 1:2.270 across 20 screens, no exceptions). Five screens at five aspect ratios makes the
  page look careless; the row only reads as evidence when it's visually regular. **The slot must be
  312×708**: the old 312×675 ratio cropped ~4.7% off the bottom, which is exactly where the tab bar
  lives — the one element this phase is studying.
- **Pick the home screen, not the first result.** Mobbin returns several screens per app. Choose the
  one whose home tab is active and whose grid is visible. Grabbing result 0 blindly is how a
  search-results page gets captioned as a home screen.
- **Name for lookup.** `output/research/screens/<app-slug>.png` — lowercase, hyphens.
- **State the source.** Every image is an `app screen` from Mobbin, or a wireframe. Say which, in the
  report and on the page. Never describe a screen from memory and never pass a wireframe off as a
  capture.
- **Wireframe beats a dead gray box.** No Mobbin, or a candidate returns `[]` after two query
  variations? Draw the recorded layout as `#F2F1EC` rectangles in the same 312×708 slot, label it
  `wireframe — capture unavailable`, and move on. What's forbidden is an empty frame with no
  explanation.
- **One visual check, at the end.** Verify the finished page once, as a whole. Per-screen vision calls
  cost more time than they catch, and most of what they "verify" is already in the capture data.
