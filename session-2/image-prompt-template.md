# Image Prompt Template

When analyzing a placeholder or generating an image prompt, use this exact format. Always respond in English. Always make output easy to copy-paste.

This template is agent-agnostic — any agent can read and follow it. Paste it verbatim; do not paraphrase the section headers.

---

```text
[PHOTOGRAPHY TYPE & SUBJECT] :
Identify the photography genre and clearly describe the exact subject shown.
Include the photography type (Commercial, Editorial, Product, Lifestyle, Beauty, etc.) and reference the subject.

[SUBJECT ACTION] (subject position)
Describe how the subject is positioned or what it is doing to avoid a floating look (standing, leaning, lying, floating, angled).

[ENVIRONMENT] –
Describe the setting and background, including the surface or base and surrounding environment or background style.

[LIGHTING] (direction, type, mood, shadows)
Explain the lighting setup: direction (front, side, back, top), type (natural, studio, softbox, neon), mood, and shadow quality.

[CAMERA] (angle, lens feel, depth of field, focus)
Describe camera perspective: angle, depth of field (shallow or deep), and focus (sharp subject, blurred background).

[TEXTURE & PROPS] (materials, surface details, added elements)
Detail visible textures, materials, environmental effects, and supporting props.

[STYLE KEYWORDS]
Summarize the overall aesthetic using short descriptive keywords.

[CONSTRAINTS]
List strict rules to preserve the original subject (no logo changes, no text edits, no shape distortion).
CRITICAL: Keep the subject exactly as shown.
```

---

## Why each section exists

| Section | It answers | Skip it and the model… |
|---|---|---|
| `[PHOTOGRAPHY TYPE & SUBJECT]` | *What is this photo for, and of?* | picks a generic subject with no commercial intent |
| `[SUBJECT ACTION]` | *How is it placed in space?* | floats the subject — the classic AI give-away |
| `[ENVIRONMENT]` | *Where is it?* | drops it on a seamless void |
| `[LIGHTING]` | *Where does light come from, what mood?* | flattens it with default frontal light |
| `[CAMERA]` | *From where, how sharp?* | gives a snapshot, not a frame |
| `[TEXTURE & PROPS]` | *What's on the surface, what else is in frame?* | loses material realism and depth cues |
| `[STYLE KEYWORDS]` | *The 5-second summary of the look* | drifts between attempts |
| `[CONSTRAINTS]` | *What must not change?* | invents text, logos, and warped shapes |

---

## How to use

1. Read the Figma file to find placeholder frames (look for "IMAGE PLACEHOLDER" text, `#F3F1EB` gray rectangles, or frames named `placeholder` / `image-*`).
2. For each placeholder, note its context: which section it's in (hero, grid card, featured collection, category bar), approximate dimensions, and surrounding content.
3. Craft a prompt using the template above, tailored to the placeholder's context.
4. Output all prompts as copy-pasteable blocks in `output/images/prompts.md`.

---

## Matching prompt to context

Read the **slot**, not just the size. A photo marketplace homepage has four kinds of slot and each wants a different prompt:

| Slot | Size (typical) | Read it as | Prompt leans toward |
|---|---|---|---|
| **Hero** | 1200×600+ | The tone-setter. Wide, dramatic, editorial. | Landscape/editorial, deep depth of field, epic scale, negative space for headline overlays |
| **Grid card** | 300–500px wide | *Inventory.* The photo the marketplace is selling. | Commercial, single clear subject, reads at thumbnail size, clean background |
| **Featured collection** | 2–4 cards together | A *curated set.* Cohesion matters more than any one frame. | Shared palette, shared lighting direction, same photographic treatment across the set |
| **Category thumbnail** | 120–200px | *A label with a picture.* Must be legible when small. | One unmistakable subject for the category (Nature → landscape, Business → office), high subject-to-frame ratio |

**Cohesion rule:** when a prompt is for a *set* (featured collection, category row), write all the prompts in that set together and keep lighting direction, colour temperature, and camera treatment consistent across them. A collection that looks like five different photographers didn't make a collection.

---

## Output format

Each prompt is a self-contained block. Wrap the prompt body in a fenced code block so the audience can copy it with one click, and precede it with a heading naming the slot.

```markdown
## Placeholder 1 — Hero Image (1200×600px)

[one line: why this prompt matches this slot]

\`\`\`text
[PHOTOGRAPHY TYPE & SUBJECT] :
...
\`\`\`
```

Rules for the output file:

- One `##` heading per placeholder, named for its section and dimensions.
- The prompt itself inside a fenced code block — no commentary inside the block.
- One short line above each block explaining the contextual read (which slot, what it's for). Keep it to one line.
- Number placeholders in document order (top of page → bottom).
- If two placeholders share a slot type and a subject, say so and vary the treatment — don't ship near-duplicate prompts.
