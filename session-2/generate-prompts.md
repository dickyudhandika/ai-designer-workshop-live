# Generate Image Prompts for Placeholders

Agent prompt. Read `session-2/image-prompt-template.md` first — this file tells you *what to do*, that file tells you *what the output must look like*.

---

## Goal

Read the Figma homepage built in Session 1. Find every image placeholder frame. For each, craft a structured image prompt using `session-2/image-prompt-template.md`. Write the results to `output/images/prompts.md`.

---

## Steps

### 1. Read the Figma file

Call `get_metadata` to find the page containing the homepage. Call `get_node` or `get_design_context` on the homepage frame to get the full node tree.

If the MCP bridge is unavailable, fall back in this order:
1. Ask the user to paste the placeholder list (section + dimensions + nearby copy) into chat.
2. Read any screenshots already in `output/figma/` (e.g. `iteration-5.png`) and infer placeholders from the layout.

Say which path you took. Never invent placeholders that aren't in the file.

### 2. Find placeholder frames

Look for all of these:

- Text nodes containing `IMAGE PLACEHOLDER`
- Frames or rectangles filled with `#F3F1EB`
- Nodes named `placeholder`, `image-*`, `img-*`, `hero-image`

Record each node's `id`, `name`, and parent chain — you need the parent to know which section it belongs to.

### 3. Extract context for each placeholder

| Field | Where it comes from |
|---|---|
| **Section** | Walk up the parent chain: hero, category bar, photo grid, featured collection, footer |
| **Dimensions** | `width × height` from the node properties |
| **Surrounding content** | Sibling text nodes — headings, card titles, photographer names, prices, category labels |
| **Grid position** | Is it the first card? A wide feature? A small thumbnail in a row? |
| **Aspect ratio** | Derive it — a 400×300 slot wants a 4:3 frame, a 1200×600 wants 2:1 |

Sort into the four slot types from the template: **hero**, **grid card**, **featured collection**, **category thumbnail**.

### 4. Craft the prompts

Match treatment to slot. Do not write four near-identical prompts.

- **Hero image:** large, editorial, dramatic. Deep depth of field or a strong single focal plane. Leave breathing room where the headline sits — describe the negative space explicitly.
- **Grid cards:** commercial photography, clean, one clear subject, background that doesn't fight the card border. This is the inventory being sold — vary subjects across cards (nature, people, business, food, architecture).
- **Featured collection:** curated and cohesive. Write the whole set in one pass. Same light direction, same colour temperature, same camera treatment. Name the shared palette.
- **Category thumbnails:** representative, unmistakable, legible at 160px. Nature = landscape, People = portrait, Business = office/desk, Food = plated dish. High subject-to-frame ratio — no busy backgrounds.

**Ground every prompt in the file.** If the card next to the placeholder reads "Misty pine forest — $12", the prompt describes a misty pine forest, not a beach. If a category chip says "Business", the thumbnail is a business scene. Context from the Figma file beats your own taste.

**Vary, don't duplicate.** If two placeholders would naturally get the same subject, change season, time of day, or framing so the grid doesn't look like one photo repeated.

### 5. Handle a set as a set

For the featured collection and the category row, write the prompts as one coherent group. Before writing, decide and state:

- Shared light direction (e.g. "soft side light from camera left, all four")
- Shared palette (e.g. "cool greens, slate, fog white")
- Shared camera treatment (e.g. "50mm, deep focus, eye level")

Then write each prompt so it honours those three.

### 6. Output

Write all prompts to `output/images/prompts.md`.

Format:

````markdown
# Image Prompts for Photo Marketplace Homepage

File: [Figma file name]
Placeholders found: [n]
Generated: [date]

---

## Placeholder 1 — Hero Image (1200×600px)

Hero slot. Wide editorial landscape sets the marketplace tone and leaves room for the headline overlay on the left third.

```text
[PHOTOGRAPHY TYPE & SUBJECT] :
Editorial landscape photography. A dramatic mountain range at golden hour...

[SUBJECT ACTION] (subject position)
...

[ENVIRONMENT] –
...

[LIGHTING] (direction, type, mood, shadows)
...

[CAMERA] (angle, lens feel, depth of field, focus)
...

[TEXTURE & PROPS] (materials, surface details, added elements)
...

[STYLE KEYWORDS]
cinematic, golden hour, epic scale, warm tones, editorial

[CONSTRAINTS]
No text overlays. No logos. No watermarks. Maintain natural colour grading. Keep the left third uncluttered for headline placement.
```

---

## Placeholder 2 — Grid Card 1 (400×300px)

Grid inventory slot, 4:3. Commercial nature stock — the kind of image the marketplace is selling.

```text
...
```
````

Every prompt must be a self-contained block the audience can copy and paste into their image provider with zero editing.

---

## Rules

- Use the exact section headers from `image-prompt-template.md`. Do not rename, reorder, or drop a section.
- Respond in English. Prompts are English regardless of the workshop language.
- No commentary inside the prompt blocks. Context line above each block, one line maximum.
- Ground prompts in the Figma file's real content — card titles, category names, prices.
- Keep style keywords to 4–7 comma-separated terms.
- Always include a `[CONSTRAINTS]` line that forbids text, logos, and watermarks. These are stock images; embedded text makes them unusable.
- Number placeholders in document order, top to bottom.
- Report the count: "Found N placeholders, wrote N prompts." If N doesn't match, say why.

## MCP Tools Used

- `get_metadata` — find the homepage page
- `get_node` / `get_design_context` — read the node tree
- `get_styles` / `get_variables` (if available) — confirm the palette the images should sit against

## Done when

- `output/images/prompts.md` exists
- Every placeholder in the file has exactly one prompt
- Every prompt has all 8 sections, in template order
- Prompt count matches placeholder count
