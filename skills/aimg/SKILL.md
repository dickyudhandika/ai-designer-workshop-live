---
name: aimg
description: Use when the user hands over a reference image to turn into a reusable prompt, or asks for the structured image-prompt format (PHOTOGRAPHY TYPE & SUBJECT, SUBJECT ACTION, ENVIRONMENT, LIGHTING, CAMERA, TEXTURE & PROPS, STYLE KEYWORDS, CONSTRAINTS).
---

# aimg

**Scan an image. Return a prompt. That's the job.**

This skill does not generate images. It reads a reference image and produces the filled eight-section prompt format, ready to paste into whatever image provider the user already uses — Midjourney, Nano Banana, DALL·E, FAL, Ideogram, Firefly, a local model.

The prompt is the deliverable. A generated image is one output of it, and that choice belongs to the person, not the agent.

## What to do

When the user supplies an image — a file path, a pasted image, a screenshot — and wants a prompt from it, or asks for the format:

1. **Look at the image.** Read the actual pixels. Describe only what is really in it; never invent a subject the image doesn't show.
2. **Fill all eight sections, in order.** Keep the bracket labels verbatim so the block stays greppable and re-usable.
3. **Return it as one copy-paste code block**, nothing wrapped around it.
4. **Copy the whole block to the clipboard** with `pbcopy` so it can be pasted straight into the user's image provider.
5. **Stop.** Do not generate an image, even if you have a generation tool available. Scan, hand back the block, done.

If the user asks only for the empty template, return the template block — not a filled one.

If the user asks you to generate an image, say plainly that this skill writes prompts rather than images, and hand back the prompt block so they can take it to their own provider.

## The format

```text
[PHOTOGRAPHY TYPE & SUBJECT] :
Identify the photography genre and clearly describe the exact subject shown.
Include the photography type (Commercial, Editorial, Product, Lifestyle, Beauty, etc.) and reference the actual subject.

[SUBJECT ACTION] (subject position)
Describe how the subject is positioned or what it is doing, to avoid a floating look (standing, leaning, lying, floating, angled).

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
List strict rules to preserve the subject and keep it usable (no text, no logos, no watermarks, no shape distortion). Keep the subject exactly as shown.
```

| Section | Drop it and the model… |
|---|---|
| `TYPE & SUBJECT` | picks a generic subject with no commercial intent |
| `SUBJECT ACTION` | floats the subject — the classic AI give-away |
| `ENVIRONMENT` | drops it on a seamless void |
| `LIGHTING` | flattens it with default frontal light |
| `CAMERA` | gives a snapshot, not a frame |
| `TEXTURE & PROPS` | loses material realism |
| `STYLE KEYWORDS` | drifts between attempts |
| `CONSTRAINTS` | invents text, logos, warped shapes |

The output is text, so it pastes into any provider with zero edits.

## Rules

- **Scanning beats guessing.** If an image is on screen, read it. Never describe a photo from memory or imagination.
- **`CONSTRAINTS` is load-bearing**, not boilerplate — it's the line that keeps a stock image sellable.
- **Clipboard after every output** (macOS): `printf '%s' "<block>" | pbcopy`. Skip silently on non-macOS; a clipboard failure must never fail the response.
- **Concise.** The block, no commentary unless asked.
- **No generation, no fallbacks.** Not a placeholder, not a mock, not an SVG or PIL stand-in. If the user wants an image, the prompt is what you give them.

## Output

The filled format block, on the clipboard.
