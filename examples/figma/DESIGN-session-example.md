# DESIGN.md — Session Adaptation (Photo Marketplace)

**Example output.** The baseline at `assets/DESIGN.md` is a dashboard system: 240px sidebar, data table, filter bar, 1200px content max-width. A photo marketplace is an image-grid product, so the baseline gets adapted — not replaced.

This is a **partial file**. Only changed sections are shown. Everything not listed here is inherited verbatim from `assets/DESIGN.md`.

---

## Change Summary

| Section | Baseline | Session adaptation | Why |
|---|---|---|---|
| `colors.primary` | `#1A5EFF` blue | `#1A5EFF` blue — **kept** | Already reserved for one CTA only. Unsplash's minimal-chrome positioning needs exactly that restraint. No reason to churn it. |
| `colors.muted` | `#F3F1EB` subtle background | **kept, repurposed** | Same value, new job: it's now the image placeholder fill, not just a section tint. |
| `colors.photo-backdrop` | *(does not exist)* | **new** `#EDEAE1` | One step darker than `muted`. Photos sit on it when a tile's aspect ratio doesn't match its slot. Slightly darker so a warm-white photo still reads as a photo, not as blank canvas. |
| Layout grid | Sidebar 240px + content | **no sidebar**, edge-to-edge grid, max-width 1440px | An image grid wants width. A 240px sidebar would waste 20% of the viewport on navigation. |
| Card grid | `repeat(auto-fill, minmax(320px, 1fr))` | `repeat(auto-fill, minmax(280px, 1fr))`, gap `lg` (16px) | Denser grid — photo marketplaces show 4–5 columns at desktop width. 320px min only yields 3–4. |
| Content max-width | 1200px | 1440px (grid areas), 720px (text blocks) | Wider canvas for the grid; text keeps a readable measure. |
| Radius | all `0px` | **kept, all `0px`** | The sharp aesthetic is deliberate and reads as precision/editorial, which suits a curated marketplace. Photos are the soft element — the frame doesn't need to be. |
| Typography | Fauna One + Inter | **kept** | Titles in Fauna One, everything else Inter. No change. |
| Components | *(dashboard set)* | **+ photo-card** (new contract) | The product's core unit doesn't exist in a dashboard system. |
| Components | Sidebar, Table, Filter bar | **excluded** | Not used in an image-grid product. |

---

## Colors (changed entries only)

```yaml
colors:
  primary: "#1A5EFF"               # KEPT. Blue. One CTA per screen — on this homepage that's the hero search submit. Not used on chips, not used on card hover.
  muted: "#F3F1EB"                 # KEPT, repurposed. Now the image placeholder fill. Also still valid for section tint.
  photo-backdrop: "#EDEAE1"        # NEW. Behind photos whose aspect ratio doesn't fill the slot. One step darker than muted so a warm-white photo separates from the surface.
  border: "#E5E2D9"                # KEPT. Separates card from card and section from section. Never wraps a photo.
```

**Rules added for this adaptation:**

- **No border around photo tiles.** The photo *is* the visual boundary. A 1px border around an image reads as a frame on a frame — decorative, which `border` is forbidden to be.
- **No shadow on photo tiles.** A shadow implies elevation. Grid cards are flush tiling surfaces; elevation is a lie. Shadows stay reserved for modals and dropdowns per the baseline.
- **`photo-backdrop` only behind images**, never as a page or section background — that's what `background` and `muted` are for.
- **`primary` appears exactly once above the fold.**

---

## Layout (changed entries only)

```yaml
layout:
  grid:
    max-width: 1440px             # CHANGED from 1200px. An image grid wants width.
    photo-grid: "repeat(auto-fill, minmax(280px, 1fr))"   # CHANGED from minmax(320px, 1fr)
    photo-grid-gap: 16px          # lg
    text-column-max-width: 720px  # kept — text measure stays readable
  sidebar:
    enabled: false                # CHANGED. Nav is a single top row, not a sidebar.
  hero:
    height: 600px                 # NEW. Full-bleed, headline overlay on the left third.
    image-slot: "1200x600"        # NEW. 2:1 editorial landscape.
  category-bar:
    height: 120px                 # NEW
    thumbnail-slot: "160x120"     # NEW. 4:3, legible at small size.
```

**Rules added for this adaptation:**

- **Photo grid is the page.** Above-the-fold budget goes to nav + search + grid. No marketing band, no hero story, no pricing block before the first row of photos.
- **Never letterbox a photo to force a grid fit.** Use `photo-backdrop` behind it and let the natural ratio stand. Cropping to a uniform shape is what the uniform-grid competitors do, and it's exactly the differentiator to avoid.
- **Section gap stays `xl` (24px) minimum** — the baseline rule holds. Between the grid and the collection band, use `3xl` (48px) so the curated band reads as a distinct chapter.
- **Chips and category tiles are not `primary`.** They're `muted` surfaces with `foreground` text. Only the search submit is `primary`.

---

## Components — Photo Card (new)

The core unit of the product. Not present in the dashboard baseline.

| Part | Element | Notes |
|---|---|---|
| `PhotoCard.Root` | `<article>` | No border, no shadow. Radius 0px. Background `photo-backdrop` behind the image only. |
| `PhotoCard.Image` | `<img>` | Fills card width. Natural aspect ratio preserved — never cropped to a fixed height. |
| `PhotoCard.Title` | `<h3>` | `label-md` (16px Inter Medium 500), `color.foreground`. One line, `text-overflow: ellipsis`. |
| `PhotoCard.Photographer` | `<span>` | `label-xs` (12px Inter Medium), `color.muted-foreground`. Sits below the title. |
| `PhotoCard.Price` | `<span>` | `label-sm` (14px Inter Medium 500), `color.foreground`. Right-aligned, same baseline row as photographer. |
| `PhotoCard.Meta` | `<div>` | Title stack left, photographer + price row beneath. Gap `sm` (8px) within, `md` (12px) between sections. |
| `PhotoCard.LicenceBadge` | `Badge` (default variant) | Optional. `muted` background, `border` outline, `label-xs`. Bottom-left over the image, `xs` (4px) inset. |

**Rules:**

- **Cards are not interactive surfaces.** No hover state on the card itself — the baseline's "cards are surfaces, not interactive" rule holds. If a click is needed, wrap in a button, and the button's hover is on the *title*, not the card.
- **No overlay gradients on card images.** The photo is the product; a scrim to make text legible is dishonest about what's being sold. Put metadata below the image, never on it.
- **Metadata order is fixed:** title → photographer → price. A buyer scans who shot it before what it costs.
- **Price only appears when a price exists.** On a free/community marketplace, omit the node entirely — don't render "Free", which reads as a badge.
- **Aspect ratios vary within the grid.** Masonry behaviour is the point. Do not set a fixed image height.
- **`LicenceBadge` uses the `default` variant only.** `primary` and `destructive` badge variants are reserved for account state and errors respectively — never for content metadata.

---

## Excluded from this adaptation

Dashboard-only, not used in an image-grid product:

- **`sidebar`** — nav is a single top row.
- **`table`** — no tabular data on the marketplace surface.
- **`filter-bar`** — filters live in a left panel inside the results view, not on the homepage.
- **`select` as a primary control** — kept in the token set for future settings surfaces, not used on the homepage.

## Pre-flight additions

Appended to the baseline checklist for this project:

- [ ] **Photo grid visible without scrolling past a marketing band?** Nav + search + first grid row must fit above the fold.
- [ ] **No border and no shadow on any photo tile?** Photos are their own boundary.
- [ ] **Exactly one `primary` element above the fold?** The hero search submit.
- [ ] **Natural aspect ratios preserved?** No forced uniform crop. `photo-backdrop` fills the remainder.
- [ ] **Metadata below the image, never on it?** No scrims, no overlays.
- [ ] **Cards use `muted`/`background`/`photo-backdrop` only?** No `primary` on chips, tiles, or metadata.
