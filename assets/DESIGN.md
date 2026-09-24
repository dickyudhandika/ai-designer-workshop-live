---
version: 1
name: ds4a-baseline
description: >-
  Warm white, sharp edges, blue accent. Inter + Fauna One. Calm professional.
  Curated taste layer for AI coding agents. Living library that compounds with every project.
colors:
  # Semantic color tokens — use by intent, not by value
  background: "#FDFCF8"            # Warm white. Main canvas. Never pure white.
  foreground: "#1A1A1A"            # Primary text. Near-black, not pure black.
  secondary: "#A1A1A1"             # Secondary gray. Mid-tone for subtle elements.
  muted: "#F3F1EB"                 # Subtle background. Sections, cards, hover states.
  border: "#E5E2D9"                # Separating content only. Never decorative.
  muted-foreground: "#A1A1A1"      # Secondary text, placeholders. Must pass AA.
  primary: "#1A5EFF"               # Blue. CTAs and active states only. Not decoration.
  primary-foreground: "#FFFFFF"    # Text on primary. White for AA contrast on blue.
  destructive: "#C73E3E"           # Errors and destructive actions only. AA with white.
typography:
  # ── Titles (Fauna One, Medium 500) ──
  title-h1:
    fontFamily: "\"Fauna One\", serif"
    fontSize: 56px
    fontWeight: 500
    lineHeight: 0.96
    letterSpacing: -0.01em
  title-h2:
    fontFamily: "\"Fauna One\", serif"
    fontSize: 48px
    fontWeight: 500
    lineHeight: 1.17
    letterSpacing: -0.01em
  title-h3:
    fontFamily: "\"Fauna One\", serif"
    fontSize: 40px
    fontWeight: 500
    lineHeight: 1.2
    letterSpacing: -0.01em
  title-h4:
    fontFamily: "\"Fauna One\", serif"
    fontSize: 32px
    fontWeight: 500
    lineHeight: 1.25
    letterSpacing: -0.005em
  title-h5:
    fontFamily: "\"Fauna One\", serif"
    fontSize: 24px
    fontWeight: 500
    lineHeight: 1.33
    letterSpacing: 0
  title-h6:
    fontFamily: "\"Fauna One\", serif"
    fontSize: 20px
    fontWeight: 500
    lineHeight: 1.4
    letterSpacing: 0
  # ── Labels (Inter, Medium 500) ──
  label-xl:
    fontFamily: "Inter, system-ui, sans-serif"
    fontSize: 24px
    fontWeight: 500
    lineHeight: 1.33
    letterSpacing: -0.015em
  label-lg:
    fontFamily: "Inter, system-ui, sans-serif"
    fontSize: 18px
    fontWeight: 500
    lineHeight: 1.33
    letterSpacing: -0.015em
  label-md:
    fontFamily: "Inter, system-ui, sans-serif"
    fontSize: 16px
    fontWeight: 500
    lineHeight: 1.5
    letterSpacing: -0.011em
  label-sm:
    fontFamily: "Inter, system-ui, sans-serif"
    fontSize: 14px
    fontWeight: 500
    lineHeight: 1.43
    letterSpacing: -0.006em
  label-xs:
    fontFamily: "Inter, system-ui, sans-serif"
    fontSize: 12px
    fontWeight: 500
    lineHeight: 1.33
    letterSpacing: 0
  # ── Paragraphs (Inter, Regular 400) ──
  paragraph-xl:
    fontFamily: "Inter, system-ui, sans-serif"
    fontSize: 24px
    fontWeight: 400
    lineHeight: 1.33
    letterSpacing: -0.015em
  paragraph-lg:
    fontFamily: "Inter, system-ui, sans-serif"
    fontSize: 18px
    fontWeight: 400
    lineHeight: 1.33
    letterSpacing: -0.015em
  paragraph-md:
    fontFamily: "Inter, system-ui, sans-serif"
    fontSize: 16px
    fontWeight: 400
    lineHeight: 1.5
    letterSpacing: -0.011em
  paragraph-sm:
    fontFamily: "Inter, system-ui, sans-serif"
    fontSize: 14px
    fontWeight: 400
    lineHeight: 1.43
    letterSpacing: -0.006em
  paragraph-xs:
    fontFamily: "Inter, system-ui, sans-serif"
    fontSize: 12px
    fontWeight: 400
    lineHeight: 1.33
    letterSpacing: 0
rounded:
  xs: 0px     # Badges, small inline elements
  sm: 0px     # Inputs, badges
  md: 0px     # Cards, buttons
  lg: 0px     # Modals, large surfaces
  full: 0px   # Not used — sharp aesthetic only
spacing:
  xs: 4px     # Tight gaps, badge padding
  sm: 8px     # Button gap, field gap, radio gap
  md: 12px    # Input padding, fieldset gap, small button padding
  lg: 16px    # Input padding, card gap, radio-card padding
  xl: 24px    # Card padding, form gap, minimum section gap
  2xl: 32px   # Section spacing
  3xl: 48px   # Page-level spacing
  4xl: 64px   # Hero spacing, major page divisions
components:
  button:
    radius: 0px
    padding-sm: "8px 12px"
    padding-md: "10px 16px"
    padding-lg: "12px 24px"
    font-size-sm: 14px
    font-size-md: 16px
    font-size-lg: 24px
    font-weight: 500
    gap: 8px
    variants: [primary, secondary, ghost]
  input:
    radius: 0px
    padding-sm: "8px 12px"
    padding-md: "12px 16px"
    padding-lg: "16px 24px"
    font-size-sm: 14px
    font-size-md: 16px
    font-size-lg: 24px
    font-weight: 400
    border: "1px solid var(--color-border)"
    variants: [default, error]
  card:
    radius: 0px
    padding: 24px
    border: "1px solid var(--color-border)"
    variants: [default, elevated, flush]
  badge:
    radius: 0px
    padding: "4px 8px"
    font-size: 12px
    font-weight: 500
    gap: 4px
    variants: [default, primary, destructive]
  field:
    label-font-size: 14px
    label-font-weight: 500
    description-font-size: 14px
    description-color: muted-foreground
    error-font-size: 14px
    error-color: destructive
    gap: 8px
  fieldset:
    legend-font-size: 16px
    legend-font-weight: 500
    gap: 12px
  form:
    gap: 24px
  select:
    radius: 0px
    padding: "12px 16px"
    font-size: 16px
    font-weight: 400
    popup-radius: 0px
    popup-padding: 4px
    popup-max-height: 280px
    icon-rotation: 180deg
  radio-group:
    gap: 8px
    radio-card-padding: 16px
    radio-card-gap: 16px
    radio-card-padding-mobile: 14px
  modal:
    radius: 0px
    padding: 24px
    width-sm: 320px
    width-md: 480px
    width-lg: 640px
    backdrop: "rgba(26, 26, 26, 0.4)"
    shadow: elevated
    header-gap: 8px
    footer-gap: 16px
    variants: [sm, md, lg]
  tabs:
    radius: 0px
    trigger-padding: "8px 12px"
    trigger-font-size: 16px
    trigger-font-weight: 500
    indicator-height: 2px
    indicator-color: primary
    list-border: "1px solid var(--color-border)"
    variants: [underline]
  table:
    radius: 0px
    row-padding: "12px 16px"
    header-font-size: 14px
    header-font-weight: 500
    header-color: muted-foreground
    cell-font-size: 14px
    cell-font-weight: 400
    row-border: "1px solid var(--color-border)"
    hover-background: muted
    selected-background: "rgba(26,94,255,0.04)"
    variants: [default]
  sidebar:
    radius: 0px
    width: 240px
    item-padding: "12px"
    item-font-size: 14px
    item-font-weight: 500
    item-gap: 8px
    section-header-padding: "8px 12px"
    section-header-font-size: 12px
    active-indicator: "2px solid var(--color-primary)"
    container-border: "1px solid var(--color-border)"
    variants: [default]
---
<!--
Project type: dashboard (financial/budget dashboard)
Mapped from: prior goal — personal finance tracker, budget overview/dashboard navigation. No type was passed to `ds4a init`.
Generated from: master-library.md (735 lines)
Output: 650 lines (88.4% of master) — DEVIATION: generator target is 30–50%.
  Reason: the mandatory verbatim frontmatter is 240 lines (33% of master) on its own.
  Frontmatter 240 + 44 guardrails (~52) + pre-flight (10) + required tables (~59)
  = ~361 lines (49%) before any rule bullet or component contract is written.
  Hitting 50% requires deleting all 9 contracts and all rule prose.
  Priority given to: all tokens, all guardrails, all checklist items, all contracts.
Contracts: Button, Input, Card, Badge, Select, Modal, Tabs, Table, Sidebar
Excluded (dashboard matrix): Field, Fieldset, Form, RadioGroup
Layout: Sidebar 240px, Card grid, Data table, Filter bar, max-width 1200px
Generated: 2026-09-20

REGENERATION: the frontmatter below is a byte-identical copy of `.ds4a/library.md`
lines 1-240. `ds4a merge` bumps the library `version` in place, which silently
desyncs this file. On any library version bump, re-run the Step 3 extraction
(frontmatter + filtered prose) rather than hand-editing here. Verify with:
  diff <(sed -n '1,240p' .ds4a/library.md) <(sed -n '1,240p' DESIGN.md)
-->

## Overview

Warm white canvas. Sharp edges. Blue accent. Calm, professional, precise.

**Clarity over decoration. Hierarchy over noise. Rhythm over randomness.** Every value exists for a reason. Every rule prevents a category of mistakes.

- **Warm white, not clinical.** `#FDFCF8` — paper-like warmth. Never override with pure white.
- **Sharp edges, not rounded.** All radius `0px`. Sharp corners convey precision and confidence; rounded corners soften and casualize.
- **Blue accent, restrained.** `#1A5EFF` on primary actions and active states only. Never decorative, never on large surfaces. One primary action per screen.
- **Two typefaces, clear roles.** Fauna One (serif) for titles — weight and character. Inter (sans) for everything else.
- **Subtle elevation.** Shadows functional, max 8% opacity. If a shadow is visible, it's too heavy.

**Philosophy:** The system is opinionated so the output doesn't need to be. Follow the rules — consistent, professional, accessible. Break them — the output degrades visibly.

## Colors

| Token | Value | Role |
|---|---|---|
| `background` | `#FDFCF8` | Main canvas. Warm white. Never pure white. |
| `foreground` | `#1A1A1A` | Primary text. Near-black. |
| `secondary` | `#A1A1A1` | Secondary gray. Mid-tone for subtle elements. |
| `muted` | `#F3F1EB` | Subtle background. Sections, cards, hover states. |
| `border` | `#E5E2D9` | Separating content only. Never decorative. |
| `muted-foreground` | `#A1A1A1` | Secondary text, placeholders. Must pass AA. |
| `primary` | `#1A5EFF` | Blue. CTAs and active states only. |
| `primary-foreground` | `#FFFFFF` | Text on primary. White for AA contrast on blue. |
| `destructive` | `#C73E3E` | Errors and destructive actions only. AA with white. |

**Rules**

- `primary` for CTAs and active states only — not decoration, not large surfaces, not borders. If it isn't the single most important action on screen, it isn't primary.
- `destructive` for errors and destructive actions only — delete, remove, validation errors. Never emphasis, never general styling.
- `background` is warm white, never pure white. The warmth reduces eye strain and reads as paper.
- `border` separates content, never decorates. If it doesn't separate two distinct content areas, it doesn't exist.
- `muted` for subtle backgrounds only — off-canvas sections, card hover, selected rows. Not for text.
- `muted-foreground` for secondary text and placeholders. Must pass WCAG AA (4.5:1). `#A1A1A1` passes on `#FDFCF8`.
- Semantic naming over appearance — `color.primary`, not `color.blue`. The name encodes intent; the agent doesn't guess.

## Typography

| Category | Font | Weight | Sizes | Job |
|---|---|---|---|---|
| **Title** | Fauna One, serif | Medium 500 | 56→20px (H1→H6) | Page titles, section headers, card titles. One H1 per page. |
| **Label** | Inter, sans-serif | Medium 500 | 24→12px (XL→XS) | Button text, field labels, badges, table headers, metadata. |
| **Paragraph** | Inter, sans-serif | Regular 400 | 24→12px (XL→XS) | Body text, descriptions, helper text, table cells. |

**Rules**

- One font family for everything except titles — Inter (web) / SF Pro (iOS). Don't introduce other fonts.
- Fauna One for titles only (H1–H6). Never body, labels, or UI text.
- `H1` appears once per page. No exceptions. Need a second large heading? Use H2.
- Labels are not content — label tokens are for short scannable text. Never paragraphs.
- Paragraphs are not labels — never paragraph tokens for button text or badges.
- Bold weight is sparing. Medium (500) for emphasis; Bold (700) only for critical emphasis. Regular (400) default for body.
- Letter spacing is negative for large text, zero for small. Large headings tighten (`-0.01em` to `-0.015em`); 12px text has `0` tracking. Values are calibrated per size — don't override.
- Line height tightens for titles, relaxes for paragraphs. Titles `0.96`–`1.4`; paragraphs `1.33`–`1.5`. Don't mix.

**Size scale**

| Token | Size | Line height | Tracking |
|---|---|---|---|
| `title-h1` | 56px | 0.96 | -0.01em |
| `title-h2` | 48px | 1.17 | -0.01em |
| `title-h3` | 40px | 1.2 | -0.01em |
| `title-h4` | 32px | 1.25 | -0.005em |
| `title-h5` | 24px | 1.33 | 0 |
| `title-h6` | 20px | 1.4 | 0 |
| `label-xl` | 24px | 1.33 | -0.015em |
| `label-lg` | 18px | 1.33 | -0.015em |
| `label-md` | 16px | 1.5 | -0.011em |
| `label-sm` | 14px | 1.43 | -0.006em |
| `label-xs` | 12px | 1.33 | 0 |
| `paragraph-xl` | 24px | 1.33 | -0.015em |
| `paragraph-lg` | 18px | 1.33 | -0.015em |
| `paragraph-md` | 16px | 1.5 | -0.011em |
| `paragraph-sm` | 14px | 1.43 | -0.006em |
| `paragraph-xs` | 12px | 1.33 | 0 |

## Layout

**Spacing — 4px base unit**

| Token | Value | Typical use |
|---|---|---|
| `xs` | 4px | Tight gaps, badge padding, icon gaps |
| `sm` | 8px | Button gap, field gap, small button padding |
| `md` | 12px | Input padding, fieldset gap, table row padding |
| `lg` | 16px | Input padding, card gap, radio-card padding |
| `xl` | 24px | Card padding, form gap, **minimum section gap** |
| `2xl` | 32px | Section spacing |
| `3xl` | 48px | Page-level spacing |
| `4xl` | 64px | Hero spacing, major page divisions |

- 4px base unit — every spacing value is a multiple of 4. No 5px, 7px, 10px, 13px.
- **Minimum space between sections: 24px (`xl`).** Never less. Cramped? Go to `2xl` or `3xl`.
- Don't invent values — the scale spans 4px–64px, enough for any layout.
- Cards use `xl` (24px) padding by default. Flush variant uses 0; content manages its own spacing.
- Use gaps, not margins — Flexbox/grid `gap` avoids margin collapse and keeps flow consistent.

**Grid**

- CSS Grid or Flexbox. No custom grid framework.
- Content max-width **1200px** for dashboards; text-heavy sub-areas may use 720px.
- **Sidebar 240px fixed**, content fills the remainder (grid `240px 1fr`).
- Card grid `repeat(auto-fill, minmax(320px, 1fr))`.
- **Filter bar** above the table, full content width, gap `lg` (16px) between controls.

## Elevation & Depth

**Shadows**

| Token | Value | Use for |
|---|---|---|
| `subtle` | `0 1px 2px rgba(0,0,0,0.04)` | Cards, default elevation. Barely visible. |
| `elevated` | `0 4px 8px rgba(0,0,0,0.08)` | Popovers, dropdowns, modals. Clearly elevated. |

- Shadows are for elevation only, never decoration. A shadow means "this sits above the content beneath it." Not elevated → no shadow.
- Max opacity 8%. Too heavy? Reduce opacity — don't remove the shadow; the elevation signal is still needed.
- `subtle` is the default for cards and static elevated surfaces. `elevated` for popovers, dropdowns, modals, tooltips.
- **Never combine border + shadow on the same element.** Border separates; shadow elevates. Choose the signal that matches intent.

**Motion**

| Token | Value | Use for |
|---|---|---|
| `duration.fast` | 150ms | Button press, toggle, hover feedback |
| `duration.smooth` | 300ms | Page transitions, modals, dropdowns |
| `ease.out` | `cubic-bezier(0.16, 1, 0.3, 1)` | Default. Natural, decelerating. |
| `ease.in-out` | `cubic-bezier(0.65, 0, 0.35, 1)` | Symmetric transitions. |

- `ease-out` default; `ease-in-out` only for symmetric transitions (open/close, expand/collapse).
- Fast (150ms) for feedback — user interacts, element responds immediately. Smooth (300ms) for transitions — content appears or disappears.
- **Never animate layout properties** (width, height, padding). Animate `transform` and `opacity` only — layout animation causes reflow and jank.

## Shapes

| Token | Value | Use for |
|---|---|---|
| `xs` | 0px | Badges, small inline elements |
| `sm` | 0px | Inputs, badges |
| `md` | 0px | Cards, buttons |
| `lg` | 0px | Modals, large surfaces |
| `full` | 0px | Not used — sharp aesthetic only |

**Why 0px?** Sharp edges convey precision and confidence. Rounded corners soften and casualize; this system chooses precision — architectural drawings, technical documents, precision instruments. Every corner is a decision: we chose sharp.

- Don't mix radius values. All elements are 0px. No 4px or 8px "for variety." The consistency is the point.
- `border-radius: 50%` only for radio/selection indicators — not avatars, not badges, not buttons.
- Override framework defaults. Tailwind defaults to `rounded-md` (6px) — set everything to `0px` explicitly.

## Components

### Button

Variants `primary` · `secondary` · `ghost`. Sizes `sm` · `md` (default) · `lg`.

| Variant | Background | Text | Use for |
|---|---|---|---|
| `primary` | `color.primary` | `color.primary-foreground` | Main action. One per section. |
| `secondary` | `color.muted` | `color.foreground` | Secondary actions. Hover darkens to border color. |
| `ghost` | transparent | `color.foreground` | Tertiary. Border appears on hover. |

| Size | Padding | Font size |
|---|---|---|
| `sm` | 8px 12px | 14px (`label-sm`) |
| `md` | 10px 16px | 16px (`label-md`) |
| `lg` | 12px 24px | 24px (`label-xl`) |

- Text uses `label` tokens (Medium 500). Icon-to-text gap `sm` (8px). Radius 0px.
- Disabled: `opacity: 0.5` + `cursor: not-allowed` + `pointer-events: none`, all variants.
- Focus: `outline: 2px solid color.primary`, `outline-offset: 2px` (all components).
- Transition 150ms `ease-out` on background-color, border-color, filter.

### Input

Variants `default` · `error`. Sizes `sm` · `md` (default) · `lg`.

| Size | Padding | Font size |
|---|---|---|
| `sm` | 8px 12px | 14px (`paragraph-sm`) |
| `md` | 12px 16px | 16px (`paragraph-md`) |
| `lg` | 16px 24px | 24px (`paragraph-xl`) |

- Text uses `paragraph` tokens (Regular 400). Border `1px solid color.border`. Radius 0px.
- Placeholder `color.muted-foreground` (`#A1A1A1`) — AA pass on `background`. Never `border` color for placeholders.
- Error variant: border and focus ring use `color.destructive`.
- Disabled: `opacity: 0.5` + `cursor: not-allowed`. Width 100% of parent — control width via the parent container.

### Card

Variants `default` · `elevated` · `flush`.

| Variant | Shadow | Padding | Use for |
|---|---|---|---|
| `default` | `shadow.subtle` | 24px (`xl`) | Standard content card, stat card. |
| `elevated` | `shadow.elevated` | 24px (`xl`) | Popovers, floating content. |
| `flush` | `shadow.subtle` | 0 | Chart/media cards; content manages its own spacing. |

- Background `color.background` (warm white). Border `1px solid color.border`. Radius 0px.
- **No hover state.** Cards are surfaces, not interactive. Need a click? Wrap with a button.
- Stat card: value in `title-h3`, label in `label-sm` + `color.muted-foreground`, gap `sm` (8px).

### Badge

Variants `default` · `primary` · `destructive`.

| Variant | Background | Text | Border | Use for |
|---|---|---|---|---|
| `default` | `color.muted` | `color.foreground` | `1px solid color.border` | Neutral labels, status. |
| `primary` | `color.primary` | `color.primary-foreground` | none | Active/positive states. |
| `destructive` | `color.destructive` | `color.primary-foreground` | none | Errors/critical. |

- Font `label-xs` (12px, Medium 500). Padding `xs sm` (4px 8px). Gap `xs` (4px). Radius 0px.
- **Inline-flex, never block-level.** `white-space: nowrap` — badge content never wraps.

### Select

| Part | Element | Notes |
|---|---|---|
| `Select.Trigger` | `<button>` | Same styling as Input — `1px solid color.border`, radius 0px, `paragraph-md`. |
| `Select.Value` | `<span>` | Selected value or placeholder. |
| `Select.Icon` | chevron SVG | Rotates 180° when open, `duration.fast`. |
| `Select.Popup` | `<div>` | `shadow.elevated`, 0px radius, max-height 280px, padding `xs` (4px). |
| `Select.Item` | `<div>` | Highlighted → `color.muted`. Selected → Medium weight + 6px blue dot. |

- Item gap 2px. Disabled item: `opacity: 0.5` + `cursor: not-allowed` + `pointer-events: none`.

### Modal

Sizes `sm` (320px) · `md` (480px, default) · `lg` (640px).

| Part | Element | Purpose |
|---|---|---|
| `Modal.Backdrop` | `<div>` | Overlay `rgba(26,26,26,0.4)`. Click closes. |
| `Modal.Container` | `<div role="dialog">` | Content surface, centered, padding `xl` (24px). |
| `Modal.Header` | `<div>` | Title (`title-h6`) + close button. Gap `sm` (8px). |
| `Modal.Body` | `<div>` | Content. Padding 0 — container padding covers it. |
| `Modal.Footer` | `<div>` | Actions, gap `lg` (16px), right-aligned. |

- Container: `color.background`, `shadow.elevated`, **no border** — elevation is the separation (border + shadow on one element is forbidden). Radius 0px.
- Padding between header, body, footer: `lg` (16px) each.
- **Backdrop blocks interaction** — `overflow: hidden` on body while open.
- Backdrop fade `duration.smooth` (300ms) `ease-out`; container entrance animates `transform` + `opacity` only.
- **Focus trap** — focus enters on open, returns to trigger on close. Esc closes. Close button is a `ghost` Button, top-right.
- **One modal at a time.** Never stack. Confirming a destructive action replaces the modal, not overlays it.
- Footer: max 2 buttons, primary action rightmost. Delete confirmations use `destructive` — never `primary`.

### Tabs

Variant `underline` only.

| Part | Element | Notes |
|---|---|---|
| `Tabs.List` | `<div role="tablist">` | Row of triggers. Bottom border `1px solid color.border`. |
| `Tabs.Trigger` | `<button role="tab">` | Padding `sm md` (8px 12px), `label-md` (16px, Medium 500). |
| `Tabs.Indicator` | `<div>` | 2px bar under the active tab, `color.primary`. |
| `Tabs.Content` | `<div role="tabpanel">` | Padding `lg` (16px) top. |

- Inactive trigger `color.muted-foreground`; active `color.foreground` + 2px `color.primary` indicator. Hover (inactive): text → `color.foreground`, no background change.
- Disabled trigger `opacity: 0.5` + `cursor: not-allowed`.
- Indicator slides `duration.smooth` (300ms) `ease-out`. Animate `transform` only — never width/position.
- **Keyboard nav** — arrows between triggers, Home/End to first/last. Each trigger tabbable.
- **No pill/boxed variants.** Underline is the convention; pills are decorative variety and this system doesn't do that. Full-width variant: triggers `flex: 1`; default is content-width.

### Table

Variant `default`. Radius 0px. No zebra striping — borders separate rows.

| Part | Element | Notes |
|---|---|---|
| `Table.Root` | `<table>` | Full-width of parent. |
| `Table.Header` | `<thead>` | Bottom border `1px solid color.border`. |
| `Table.Row` | `<tr>` | Bottom border `1px solid color.border`. |
| `Table.HeaderCell` | `<th>` | `label-sm` (14px, Medium 500), `color.muted-foreground`. No background. |
| `Table.Cell` | `<td>` | `paragraph-sm` (14px, Regular 400), `color.foreground`. |

- Row padding `md lg` (12px 16px). One density only.
- **Row hover: background `color.muted`.** Hover signals interactivity — if rows aren't clickable, no hover.
- Selected row `rgba(26,94,255,0.04)` (blue tint). Row selection: 16px checkbox in the leftmost column (grown-checkbox contract if present, else a plain checkbox input).
- **Sort state:** chevron + `label-sm` weight on the active column. One sort column at a time.
- Numeric columns right-aligned, text columns left-aligned. Never center data.
- **Empty state:** single row, `paragraph-sm` `color.muted-foreground`, centered, "No results" + optional action link. Never a bare empty `<tbody>`.
- **Loading state:** first 3–5 rows as skeleton bars (`color.muted` blocks, `duration.fast` pulse). Never a spinner overlay.
- `overflow-x: auto` if columns exceed width — never shrink cells below their padding.

### Sidebar

Variant `default`.

| Part | Element | Purpose |
|---|---|---|
| `Sidebar.Container` | `<nav>` | Fixed 240px column. Border-right `1px solid color.border`. |
| `Sidebar.Header` | `<div>` | Logo/brand block. Padding `lg` (16px). |
| `Sidebar.Section` | `<div>` | Group of items under a section header. |
| `Sidebar.SectionHeader` | `<div>` | `label-xs` (12px, Medium 500), `color.muted-foreground`, uppercase. |
| `Sidebar.Item` | `<a>` | Padding `md` (12px). Gap `sm` (8px) icon→label. Icon 16px. |
| `Sidebar.Footer` | `<div>` | Bottom block. User menu, collapse trigger. |

- Width 240px fixed; content fills the rest (grid `240px 1fr`). Item `label-sm` (14px Medium 500), `color.foreground`.
- Hover: background `color.muted`, text stays `color.foreground`.
- Active: background `color.muted` + 2px `color.primary` left-edge indicator. Indicator is an inset border — not a pill, not a background fill. Radius 0px.
- Section header padding `sm md` (8px 12px); gap between sections `lg` (16px). **Section headers are not links.**
- Container background `color.background` — same as canvas. The border separates, not a tint.
- Disabled item `opacity: 0.5` + `cursor: not-allowed`.
- Mobile (< 768px): sidebar collapses behind a hamburger into a full-height overlay (Modal elevation + backdrop rules). Never render a squished 240px column.
- Collapse trigger (desktop, optional): icon-only `ghost` Button. Collapsed = 64px, icons only. Transition `duration.smooth` on width.

## Do's and Don'ts

**Color**

- ✅ Do use `primary` only for the single most important action on a screen.
- ✅ Do use `destructive` only for errors and destructive actions.
- ✅ Do use `muted-foreground` for placeholder text — it passes AA.
- ✅ Do use `border` only to separate distinct content areas.
- ❌ Don't override `background` with pure white (`#FFFFFF`).
- ❌ Don't use `primary` for decoration, borders, or large surface fills.
- ❌ Don't use `destructive` for emphasis or general styling.
- ❌ Don't use `border` color for placeholder text — use `muted-foreground`.

**Typography**

- ✅ Do use Fauna One for titles (H1–H6) only.
- ✅ Do use label tokens for button text, field labels, badges, table headers.
- ✅ Do use paragraph tokens for body text, descriptions, helper text, table cells.
- ✅ Do default to Medium (500) for emphasis. Use Bold (700) sparingly.
- ❌ Don't use more than one H1 per page. No exceptions.
- ❌ Don't use label tokens for body content or paragraph tokens for labels.
- ❌ Don't use Fauna One for body text, labels, or UI elements.
- ❌ Don't use Bold (700) for general emphasis — use Medium (500).

**Spacing**

- ✅ Do use the spacing scale for every spacing decision.
- ✅ Do maintain minimum 24px (`xl`) between sections.
- ✅ Do use Flexbox/Grid `gap` over margins.
- ❌ Don't invent spacing values outside the 4px scale.
- ❌ Don't use values like 5px, 7px, 10px, 13px — they break the rhythm.

**Radius**

- ✅ Do use 0px for all elements. The sharp aesthetic is deliberate.
- ❌ Don't mix radius values. No 4px or 8px "for variety."
- ❌ Don't use `border-radius: 50%` except for radio/selection indicators.

**Shadows**

- ✅ Do use `shadow.subtle` for cards and default elevation.
- ✅ Do use `shadow.elevated` for popovers, dropdowns, and modals.
- ✅ Do reduce opacity if a shadow looks heavy — don't remove it entirely.
- ❌ Don't use shadows for decoration.
- ❌ Don't combine border + shadow on the same element for the same purpose.
- ❌ Don't exceed 8% opacity on shadows.

**Accessibility**

- ✅ Do ensure all text passes WCAG AA (4.5:1 minimum).
- ✅ Do use `muted-foreground` for placeholder text — it's calibrated for AA.
- ✅ Do use `opacity: 0.5` + `cursor: not-allowed` + `pointer-events: none` for disabled states.
- ✅ Do provide visible focus rings (`outline: 2px solid color.primary`).
- ✅ Do use semantic HTML (`<label>`, `<fieldset>`, `<legend>`, `aria-live` for errors).
- ❌ Don't change text color for disabled states — use opacity only.
- ❌ Don't eyeball contrast — use a contrast calculator.
- ❌ Don't remove focus outlines without providing an alternative.

**Components**

- ✅ Do limit one `primary` button per section.
- ✅ Do use `secondary` for alternative actions, `ghost` for tertiary.
- ✅ Do keep cards non-interactive — wrap with a button if a click is needed.
- ✅ Do use `inline-flex` for badges — never block-level.
- ❌ Don't add hover states to cards — they're surfaces, not interactive.
- ❌ Don't use badge `primary` variant for anything except active/positive states.

## Pre-flight Checklist

Before generating any UI, verify:

- [ ] **One primary action per screen?** Only one element uses `color.primary` as background.
- [ ] **Spacing follows the 4px grid?** No invented values. All spacing from `xs` to `4xl`.
- [ ] **Semantic tokens used, not raw values?** No `#1A5EFF` in markup — use `color.primary` or `var(--color-primary)`.
- [ ] **WCAG AA checked?** All text passes 4.5:1. Placeholder text uses `muted-foreground`.
- [ ] **H1 appears once?** Exactly one `title-h1`. Additional headings use H2+.
- [ ] **Radius values from scale?** All elements use 0px. No invented radius.
- [ ] **Shadows for elevation only?** No decorative shadows. Max 8% opacity.
- [ ] **Typography categories respected?** Titles in Fauna One. Labels and paragraphs in Inter.
- [ ] **Disabled states use opacity?** No color changes for disabled — `opacity: 0.5` only.
- [ ] **Border for separation, not decoration?** Every border separates distinct content areas.
