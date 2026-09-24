# Phase 2 — Assign Design Tokens to Figma

Agent prompt. **10 minutes.** This is the MCP proof moment — the most detailed prompt in the repo. Follow it in order.

---

## Goal

Read `assets/DESIGN.md`, create real Figma design tokens (variable collections + named text styles) via MCP. The audience watches tokens appear live in Figma's sidebar.

Everything below is derived from `assets/DESIGN.md`. If the file and this prompt disagree, **the file wins** — re-read it, don't trust this page.

---

## Steps

### 1. Read `assets/DESIGN.md`

Parse the YAML frontmatter. Extract two things:

- **Colors** — 9 semantic tokens with hex values
- **Typography** — 16 styles with `fontFamily`, `fontSize`, `fontWeight`, `lineHeight`, `letterSpacing` (6 titles, 5 labels, 5 paragraphs)

Read `rounded` and `spacing` too — you'll use them in Phase 3, not here.

**Count the tokens yourself, from the file.** This prompt and the workshop brief both quote counts; the YAML frontmatter is the only authority. If the numbers disagree, use the file's numbers and say what you found.

### 2. Create a Figma page named `Design System`

Call `create_page` with name `Design System`.

### 3. Create the color variable collection

Call `create_variable_collection` with name `Colors`. Save the returned `collectionId` and `modeId` — every subsequent variable call needs them.

### 4. Create the 9 color variables

Call `create_variables` once, batched, with the collection ID. Pass **hex strings for COLOR type** — the tool converts them.

| Name | Hex | Intent |
|---|---|---|
| `background` | `#FDFCF8` | Warm white. Main canvas. Never pure white. |
| `foreground` | `#1A1A1A` | Primary text. Near-black, not pure black. |
| `secondary` | `#A1A1A1` | Mid-tone gray for subtle elements. |
| `muted` | `#F3F1EB` | Subtle background. Sections, cards, hover. |
| `border` | `#E5E2D9` | Separating content only. Never decorative. |
| `muted-foreground` | `#A1A1A1` | Secondary text, placeholders. |
| `primary` | `#1A5EFF` | Blue. CTAs and active states only. |
| `primary-foreground` | `#FFFFFF` | Text on primary. |
| `destructive` | `#C73E3E` | Errors and destructive actions only. |

Note `secondary` and `muted-foreground` share the same hex. They are different **intents** with the same value — keep both, do not collapse them. That distinction is the whole point of a semantic token layer.

### 5. Create visual color swatches

On the `Design System` page, create a frame named `Color Swatches`:

- `create_frame` with the container
- `set_auto_layout` — direction horizontal, wrap on, gap 16, padding 24

For each of the 9 colors, create a swatch group:

- A frame 100×80px, then `set_solid_fill` with that color's hex
- A `create_text` node below it with two lines: token name and hex (e.g. `background` / `#FDFCF8`)
- Use `foreground` for the label text so it stays legible on the page

Add a 1px `border`-colored outline on each swatch frame where the fill is light, so `background`, `muted`, and `primary-foreground` are visible against the page.

### 6. Create the text styles

For each typography token in the file, call `create_text_style`. Name = title-cased token name (`title-h1` → `Title H1`, `label-md` → `Label MD`, `paragraph-sm` → `Paragraph SM`).

**The conversions matter.** Two rules:

- **lineHeight → PERCENT.** DESIGN.md ratios are unitless (0.96, 1.17). Pass `{value: <ratio × 100>, unit: "PERCENT"}`. So `1.17` → `{value: 117, unit: "PERCENT"}`.
- **letterSpacing → px number.** DESIGN.md values are in `em`. Multiply by the font size. `-0.01em` at 56px → `-0.56`. `0` stays `0`.

| Style name | Token | Font family | Size | Weight | lineHeight | letterSpacing |
|---|---|---|---|---|---|---|
| `Title H1` | title-h1 | Fauna One | 56 | 500 | `{value: 96, unit: "PERCENT"}` | `-0.56` |
| `Title H2` | title-h2 | Fauna One | 48 | 500 | `{value: 117, unit: "PERCENT"}` | `-0.48` |
| `Title H3` | title-h3 | Fauna One | 40 | 500 | `{value: 120, unit: "PERCENT"}` | `-0.40` |
| `Title H4` | title-h4 | Fauna One | 32 | 500 | `{value: 125, unit: "PERCENT"}` | `-0.16` |
| `Title H5` | title-h5 | Fauna One | 24 | 500 | `{value: 133, unit: "PERCENT"}` | `0` |
| `Title H6` | title-h6 | Fauna One | 20 | 500 | `{value: 140, unit: "PERCENT"}` | `0` |
| `Label XL` | label-xl | Inter | 24 | 500 | `{value: 133, unit: "PERCENT"}` | `-0.36` |
| `Label LG` | label-lg | Inter | 18 | 500 | `{value: 133, unit: "PERCENT"}` | `-0.27` |
| `Label MD` | label-md | Inter | 16 | 500 | `{value: 150, unit: "PERCENT"}` | `-0.176` |
| `Label SM` | label-sm | Inter | 14 | 500 | `{value: 143, unit: "PERCENT"}` | `-0.084` |
| `Label XS` | label-xs | Inter | 12 | 500 | `{value: 133, unit: "PERCENT"}` | `0` |
| `Paragraph XL` | paragraph-xl | Inter | 24 | 400 | `{value: 133, unit: "PERCENT"}` | `-0.36` |
| `Paragraph LG` | paragraph-lg | Inter | 18 | 400 | `{value: 133, unit: "PERCENT"}` | `-0.27` |
| `Paragraph MD` | paragraph-md | Inter | 16 | 400 | `{value: 150, unit: "PERCENT"}` | `-0.176` |
| `Paragraph SM` | paragraph-sm | Inter | 14 | 400 | `{value: 143, unit: "PERCENT"}` | `-0.084` |
| `Paragraph XS` | paragraph-xs | Inter | 12 | 400 | `{value: 133, unit: "PERCENT"}` | `0` |

Font family strings: pass `Fauna One` for the six titles and `Inter` for the ten labels/paragraphs. DESIGN.md writes them as CSS stacks (`"Fauna One", serif`, `Inter, system-ui, sans-serif`) — strip the stack and pass the primary family name only.

Optionally bind the text styles to the color variables via the `variableBindings` parameter on `create_text_style` where the tool supports it (e.g. `foreground` for body styles).

### 7. Create the typography preview

Create a frame named `Typography Scale`:

- `set_auto_layout` — direction vertical, gap 20, padding 24

For each of the styles in the table, add a `create_text` node:

- Content: the style name plus its size — `Title H1 — 56px`
- Apply the matching `fontFamily` / `fontSize` / `fontWeight` from the table, so the preview is visually truthful rather than labeled only

### 8. Screenshot the result

Call `save_screenshots` with the `Design System` page `nodeId` and `outputPath` = `output/figma/tokens-baseline.png`.

If the tool writes to a default location instead, copy the file to `output/figma/tokens-baseline.png` afterwards and say so.

### 9. PAUSE

Present the screenshot **and** ask the room to look at their own Figma window — the variables and text styles should be visibly present in the sidebar. Let the audience see the tokens live in Figma before continuing to Phase 3.

State plainly: 1 page, 1 variable collection, 9 color variables, 1 color swatch frame, N text styles (count them), 1 typography preview frame. If any number doesn't match what's actually in the file, say which and why.

---

## MCP tools used

| Tool | Purpose |
|---|---|
| `create_page` | Create the Design System page |
| `create_variable_collection` | Create the Colors collection |
| `create_variables` | Batch-create 9 color variables (hex for COLOR) |
| `create_frame` | Containers for swatches and typography scale |
| `set_solid_fill` | Apply color to swatch frames |
| `set_auto_layout` | Horizontal wrap for swatches, vertical stack for type |
| `create_text` | Swatch labels and typography previews |
| `create_text_style` | Named Figma text styles, one per typography token |
| `set_bound_variable` | Bind variables to nodes where applicable |
| `save_screenshots` | Export `output/figma/tokens-baseline.png` |

## Error handling

| Failure | Response |
|---|---|
| `Fauna One could not be loaded` from `create_text_style` | **Expected.** Retry the affected style with fontFamily `Playfair Display`. Inter stays as-is. Note the substitution in the artifact and in the Phase 3 log. |
| `create_variables` batch fails | Retry the 9 colors individually, one call each. Report the count that landed. |
| `fileKey` starts with `unsaved-` | Proceed normally. All read/write operations work on unsaved local files. If the session ends without a save, tokens are lost — tell the room to save the Figma file. |
| Figma MCP unavailable entirely | Degrade: write `output/figma/tokens.json` (all 9 colors + every typography style, resolved values) plus an HTML swatch sheet into `output/figma/`. Say which path you took. |

## Done when

- `Design System` page exists in Figma with the collection, 9 variables, swatches, the text styles, and the typography preview
- `output/figma/tokens-baseline.png` exists
- The count reported in chat matches what's actually in the file
- The room has seen it before Phase 3 starts
