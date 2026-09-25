---
name: DESIGN.md → Figma token handoff
source: ./DESIGN.md (ds4a-baseline v1, generated 2026-09-20)
target: Figma file "Halodesigner test 2" (unsaved-mugd68hs-bwitfzvq)
frame: 9:427 "Variation E — Shoppable tiles (tokenized)", 390×844, page "Mobbin — Photo Showcase Homes" (4:440)
tokens_page: 9:385 "00 Tokens"
tokens_board: 9:613 "00 Tokens / foundation proof"
built: 2026-09-25
---

# What was done

The selected frame was rebuilt from scratch as an auto-layout composition and every color,
spacing, radius, and type value on it resolves from a Figma variable or text style instead of a
hardcoded number. The token foundation itself lives on a new `00 Tokens` page.

`source: ./DESIGN.md` remains the single source of truth. Change a value there, change it here —
this file records the mapping, not a second copy of the spec.

# Token foundation

Page `00 Tokens` (id `9:385`). 4 variable collections, 36 variables, 16 text styles, 2 effect styles.

## Collections

| Collection | id | Variables | Notes |
|---|---|---|---|
| `color` | `VariableCollectionId:9:386` | 9 COLOR | one mode (`9:0`) |
| `spacing` | `VariableCollectionId:9:387` | 8 FLOAT | one mode (`9:1`) |
| `radius` | `VariableCollectionId:9:388` | 5 FLOAT | all `0` |
| `typography` | `VariableCollectionId:9:530` | 14 FLOAT | 7 `font-size/*` + 7 `line-height/*` |

Figma Starter allows one mode per collection, so no light/dark modes exist. Add modes only after
upgrading the plan.

## color — `color/*`

| Name | Variable id | Value |
|---|---|---|
| `color/background` | `VariableID:9:389` | `#FDFCF8` |
| `color/foreground` | `VariableID:9:390` | `#1A1A1A` |
| `color/secondary` | `VariableID:9:391` | `#A1A1A1` |
| `color/muted` | `VariableID:9:392` | `#F3F1EB` |
| `color/border` | `VariableID:9:393` | `#E5E2D9` |
| `color/muted-foreground` | `VariableID:9:394` | `#A1A1A1` |
| `color/primary` | `VariableID:9:395` | `#1A5EFF` |
| `color/primary-foreground` | `VariableID:9:396` | `#FFFFFF` |
| `color/destructive` | `VariableID:9:397` | `#C73E3E` |

## spacing — `spacing/*`

`xs 4` `sm 8` `md 12` `lg 16` `xl 24` `2xl 32` `3xl 48` `4xl 64`
→ `VariableID:9:403` … `VariableID:9:410`

## radius — `radius/*`

`xs` `sm` `md` `lg` `full` — all `0` → `VariableID:9:398` … `VariableID:9:402`

## typography — `font-size/*` and `line-height/*`

14 variables, derived from the DESIGN.md size scale (font size × line-height, rounded to px):

| Text style | fontSize var | lineHeight var | px |
|---|---|---|---|
| `title-h6` | `font-size/title-h6` `9:531` | `line-height/title-h6` `9:538` | 20 / 28 |
| `label-md` | `font-size/label-md` `9:532` | `line-height/label-md` `9:539` | 16 / 24 |
| `label-sm` | `font-size/label-sm` `9:533` | `line-height/label-sm` `9:540` | 14 / 20 |
| `label-xs` | `font-size/label-xs` `9:534` | `line-height/label-xs` `9:541` | 12 / 16 |
| `paragraph-md` | `font-size/paragraph-md` `9:535` | `line-height/paragraph-md` `9:542` | 16 / 24 |
| `paragraph-sm` | `font-size/paragraph-sm` `9:536` | `line-height/paragraph-sm` `9:543` | 14 / 20 |
| `paragraph-xs` | `font-size/paragraph-xs` `9:537` | `line-height/paragraph-xs` `9:544` | 12 / 16 |

Only the sizes the frame actually uses were turned into variables. The full 16-entry type scale
exists as **text styles** (below), which is the right primitive for whole-style changes; the
variables exist so a single number can be re-pointed on a live node.

## Text styles — 16, named exactly as DESIGN.md names them

`title-h1` `title-h2` `title-h3` `title-h4` `title-h5` `title-h6` (Fauna One Regular 56→20)
`label-xl` `label-lg` `label-md` `label-sm` `label-xs` (Inter Medium 24→12)
`paragraph-xl` `paragraph-lg` `paragraph-md` `paragraph-sm` `paragraph-xs` (Inter Regular 24→12)

Each carries the DESIGN.md line height and letter spacing, e.g. `label-md` = Inter Medium 16 /
line-height 150% / tracking −1.1%; `title-h6` = Fauna One Regular 20 / 140% / 0.

## Effect styles — 2

| Name | Effect |
|---|---|
| `effect/subtle` | `DROP_SHADOW` `0 1px 2px` rgba(0,0,0,0.04) |
| `effect/elevated` | `DROP_SHADOW` `0 4px 8px` rgba(0,0,0,0.08) |

# Frame 9:427 — structure

108 nodes: 63 frames, 38 text, 7 vectors. **0 rectangles** — every icon placeholder was replaced
with a Phosphor vector. Root is auto-layout `VERTICAL`, fixed 390×844, 10 children in visual order.
Every section frame is fixed-size with explicit padding and gaps.

| # | Node | Size | Layout |
|---|---|---|---|
| 1 | `E/Top bar` (`9:428`) | 390×54 | HORIZONTAL, pad 16/16/16/16, `SPACE_BETWEEN` |
| 2 | `E/Top bar rule` (`9:429`) | 390×1 | border token fill |
| 3 | `E/Search section` (`9:430`) | 390×68 | VERTICAL, pad 12/16/12/16 |
| 4 | `E/Chips` (`9:432`) | 390×40 | HORIZONTAL, gap 8, pad 8/16/8/16 |
| 5 | `E/Section header row 1` (`9:431`) | 390×44 | HORIZONTAL, pad 8/16/8/16, `SPACE_BETWEEN` |
| 6 | `E/Grid 1` (`9:433`) | 390×308 | VERTICAL, gap 12, two 148-tall rows of two 172-wide tiles |
| 7 | `E/Section header row 2` (`9:434`) | 390×44 | as row 1 |
| 8 | `E/Grid 2` (`9:435`) | 390×220 | VERTICAL, gap 12, two 104-tall rows of two 172-wide tiles |
| 9 | `E/Tab bar rule` (`9:436`) | 390×1 | border token fill |
| 10 | `E/Tab bar` (`9:437`) | 390×64 | HORIZONTAL, pad 8/16/8/16, `SPACE_BETWEEN` |

Section heights sum to exactly 844. Full-tree scan: **0 overflow, 0 clipping**.

Each tile is `VERTICAL`: image area (`E/Tile n / image`) + meta row (`E/Tile n / meta`, 172×44).
The price badge (`E/Tile n / price badge`) is the image area's only auto-layout child, placed
bottom-right by `primaryAxisAlignItems: MAX` / `counterAxisAlignItems: MAX` inside the image's
12px padding — no absolute positioning anywhere.

# Binding counts

| Field | Binds |
|---|---|
| `fill` (color variables) | 101 |
| `cornerRadius` (`radius/md`) | 63 |
| `padding*` + `itemSpacing` (spacing) | 191 |
| `fontSize` (typography) | 28 |
| `lineHeight` (typography) | 20 |

Node census by fill: `#FDFCF8` ×33, `#A1A1A1` ×21, `#1A1A1A` ×20, `#F3F1EB` ×20, `#1A5EFF` ×4,
`#E5E2D9` ×2, `#FFFFFF` ×1. Every one of those is a token value; **zero off-token colors**.

# Verification evidence

Screenshots in `out/library/` (relative to the MCP server working dir,
`/Users/thenom4design/Documents/monetization/halodesigner-talk-AI-Assistant`).

| File | What it proves |
|---|---|
| `tokens-foundation-proof.png` | The whole foundation board: 9 swatches, 8 spacing bars, 5 radius squares, 16 type rows, 2 effect cards |
| `tokenized-frame-final.png` | The rebuilt frame, tokenized, with Phosphor icons |
| `tokenized-topbar.png` `tokenized-grid.png` `tokenized-tabbar.png` `tokenized-searchfield.png` | Section detail (icons at 4–6× scale) |
| `mutation-proof-before/probe/reverted.png` | `color/primary` → `#FF0000` repainted the "All" chip, both top-bar icons, both "See all" labels and the active tab icon; revert restored it |
| `font-proof-before/probe/reverted.png` | `font-size/label-md` 16 → 40 resized the "Halo Market" title; revert restored it |
| `radius-proof-probe/reverted.png` | `radius/md` 0 → 12 rounded the chip row; revert returned sharp corners |
| `spacing-proof-before/probe/reverted.png` | `spacing/md` 12 → 32 changed the grid gap; revert restored it |

Byte-level proof that the variables actually drive render: `mutation-proof-before.png` and
`mutation-proof-reverted.png` are byte-identical (md5 `98a6d836e7e119c092a6bfa7dbff9330`);
the probe render differs.

# Deviations from DESIGN.md

Each entry names the rule it departs from. Anything not listed is followed.

1. **`#A1A1A1` does not pass WCAG AA — measured 2.52:1.**
   DESIGN.md, Colors: "`muted-foreground` for secondary text and placeholders. Must pass WCAG AA
   (4.5:1). `#A1A1A1` passes on `#FDFCF8`." Measured contrast `#A1A1A1` on `#FDFCF8` = **2.52:1**;
   on `#F3F1EB` = **2.29:1**. Required = 4.5:1 for normal text. The claim in DESIGN.md is wrong.
   Consequence in this frame: **15 text nodes fail AA** — `E/Search placeholder` (`9:444`), the 3
   inactive chip labels (`9:449`, `9:451`, `9:453`), all 8 `E/Tile n / category` labels
   (`9:464` `9:471` `9:479` `9:486` `9:494` `9:501` `9:509` `9:516`), and the 3 inactive tab labels
   (`9:523` `9:526` `9:529`). The 8 price-badge labels (`9:462` etc.) are `color/foreground` on
   `color/muted` = **15.41:1** and pass. The 6 `#A1A1A1` rectangles are icons, not text, so AA text
   contrast does not apply to them (3:1 non-text contrast is the relevant bar, which they also
   miss at 2.52:1 — worth fixing in the same pass).
   I did **not** change the token. DESIGN.md is the source of truth and this is its own stated
   value; silently "fixing" it would desync the file from the library. `#6E6E6E` on `#FDFCF8`
   measures 5.0:1 and `#767676` measures 4.6:1 — a one-line change in DESIGN.md plus a
   `color/muted-foreground` variable update fixes every instance at once. Needs your call.

2. **Chips are pill-free but not radius-`full`.** DESIGN.md, Shapes: "Don't mix radius values. All
   elements are 0px." Satisfied. But the standing project rule (design-memory
   `r-radius-restrained`) allows chips/badges/tags to be pill. I kept chips at `radius/md` (0px)
   because DESIGN.md's own Components table sets `badge.radius: 0px` and its Shapes section says
   `full` is "Not used — sharp aesthetic only". Recorded, not contested — flagging because the two
   sources disagree and the file wins.

3. **Cards carry the "border + shadow" combination.** DESIGN.md, Elevation: "Never combine border
   + shadow on the same element. Border separates; shadow elevates." And Card: "Background
   `color.background`. Border `1px solid color.border`." The card contract and the elevation rule
   contradict each other for the `default` variant, which by its own table has both
   `shadow.subtle` and a border. I gave the 8 tiles `effect/subtle` with **no border** (image area
   uses `color/muted` fill to separate instead), i.e. I followed the elevation rule. If you want
   the literal card contract, add the border and drop the shadow — one line each way.

4. **Tile grid gap is `spacing/md` (12px), not a spec'd value.** DESIGN.md, Layout: "**Minimum
   space between sections: 24px (`xl`).** Never less." The 12px gap is inside a card-like tile
   grid, not between page sections. Vertical rhythm between sections in this frame is governed by
   the section frames' own padding (8–16px), which is below the 24px minimum. This is a mobile
   390px frame; 24px section gaps would not fit the reference it recreates. Both gaps are bound to
   spacing tokens, so re-pointing them is a variable change, not a redesign.

5. **~~Icon shapes are rectangles, not vectors.~~ RESOLVED.** All 7 icon placeholders are now
   Phosphor (regular weight) vectors imported via `import_html_layers` as `SVG` layers
   (`figma.createNodeFromSvg`), each wrapped in a FRAME and recolored from tokens:

   | Node | Icon | Size | Fill |
   |---|---|---|---|
   | `E/Icon search` (`9:794`) | `magnifying-glass` | 20 | `color/muted-foreground` |
   | `E/Icon profile` (`9:792`) | `user` | 20 | `color/muted-foreground` |
   | `E/Search icon` (`9:782`) | `magnifying-glass` | 16 | `color/muted-foreground` |
   | `E/Tab icon 1` (`9:780`) | `house` | 24 | `color/primary` |
   | `E/Tab icon 2` (`9:778`) | `magnifying-glass` | 24 | `color/muted-foreground` |
   | `E/Tab icon 3` (`9:776`) | `bookmark-simple` | 24 | `color/muted-foreground` |
   | `E/Tab icon 4` (`9:774`) | `user` | 24 | `color/muted-foreground` |

   Source: `@phosphor-icons/core@2.1.1` `assets/regular/*.svg` (256×256 viewBox), cached in
   `out/icons/`. Frame now contains **0 RECTANGLE nodes** — 108 nodes total: 63 frames, 38 text,
   7 vectors. Only the active tab icon uses `color/primary`, which is the system's sanctioned use
   for active states.

6. **Effect styles are not applied to the tiles.** `effect/subtle` and `effect/elevated` exist in
   the file (proven on the foundation board), but Figma's `setEffectStyleIdAsync` is not exposed by
   this MCP bridge, so the 8 tiles carry the equivalent literal effect rather than a style link.
   Changing the tile shadow today means editing the effect style *and* the tiles. Fixing this
   properly needs a bridge method for effect-style assignment.

7. **`E/Top bar` and `E/Tab bar` heights are 54 and 64, not the original 52 and 62.** DESIGN.md,
   Layout: 4px base unit, no invented values. Enforcing 4px-multiple padding (16px) plus a
   font-size-appropriate icon box forced a 2px change on each. Both are `VERTICAL`/`HORIZONTAL`
   sections inside a fixed 844 root and sum correctly; the alternative was 2px padding values,
   which violates the 4px rule outright. Chose the rule over the pixel.

# DESIGN.md pre-flight checklist — item by item

Run against frame `9:427`.

| # | Item | Result |
|---|---|---|
| 1 | One primary action per screen? Only one element uses `color.primary` as background | **PASS** — exactly one: `E/Chip All` (`9:446`). `color/primary` also fills 3 icons and 2 "See all" labels as *text/icon* color, which the color rules permit ("CTAs and active states"). |
| 2 | Spacing follows the 4px grid? No invented values | **PASS** — every padding/gap is 4, 8, 12, or 16, all bound to spacing variables. No 5/7/10/13. |
| 3 | Semantic tokens used, not raw values? | **PASS** — zero off-token hex in the frame (scan: 7 distinct fills, all token values). |
| 4 | WCAG AA checked? All text passes 4.5:1 | **FAIL** — see Deviation 1. `#A1A1A1` measures 2.52:1 on the canvas. 15 text nodes affected. |
| 5 | H1 appears once? | **PASS** — the frame contains no `title-h1`. Its largest type is `title-h6` (section headers, ×2), which is correct for a mobile app screen with no page title. |
| 6 | Radius values from scale? All elements 0px | **PASS** — 63 `cornerRadius` binds, all `radius/md` = 0. No 4px/8px, no `50%`. |
| 7 | Shadows for elevation only? Max 8% opacity | **PASS** — `effect/subtle` at 4%, `effect/elevated` at 8%, nothing above. |
| 8 | Typography categories respected? Titles Fauna One, labels/paragraphs Inter | **PASS** — `E/Section header 1`/`2` are Fauna One; all other text Inter. No Fauna One in body text. |
| 9 | Disabled states use opacity? | **PASS (vacuously)** — the frame contains no disabled element. If disabled states are added, use `opacity: 0.5` only. |
| 10 | Border for separation, not decoration? | **PASS** — 2 borders total: `E/Top bar rule` and `E/Tab bar rule`, each separating two distinct regions. The 8 price badges carry `1px color/border`, per the badge contract's `default` variant. |

# Suggested next steps

1. Decide on Deviation 1. `color/muted-foreground` from `#A1A1A1` to `#6E6E6E` (5.0:1) or
   `#767676` (4.6:1) clears AA for all 15 text nodes with one variable update; DESIGN.md needs the
   same edit or it will keep asserting the wrong contrast. The 6 muted-foreground icon
   rectangles would clear the 3:1 non-text bar at the same time.
2. Re-point Deviation 4's two gaps (`spacing/md` on grids, section padding) if you want literal
   24px section rhythm.
3. ~~Add real SVG icons (Deviation 5)~~ — done, Phosphor regular weight, token-colored.
4. If you want the whole system reusable, build the 9 component contracts as real Figma
   COMPONENT nodes on this page and publish the library. That is a user action in Figma.
