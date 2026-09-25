---
name: aimg
description: Use when the user invokes /aimg, hands over a reference image to turn into a prompt, or needs the structured image-prompt format (PHOTOGRAPHY TYPE & SUBJECT, SUBJECT ACTION, ENVIRONMENT, LIGHTING, CAMERA, TEXTURE & PROPS, STYLE KEYWORDS, CONSTRAINTS).
---

# aimg

Two jobs, and the analysis one comes first:

1. **Scan an image** and return the filled eight-section prompt format.
2. **Generate an image** from a prompt.

The format is the asset. A generated image is one output of it.

## Job 1 — scan an image into a prompt

Use when the user supplies an image (a file path, a pasted image, a screenshot) and wants a prompt from it, or asks to recover the format.

1. **Look at the image.** Describe only what is actually in it. Never invent a subject the image doesn't show.
2. **Fill all eight sections, in order.** Keep the bracket labels verbatim so the block stays greppable and re-usable.
3. **Return it as one copy-paste code block**, nothing wrapped around it.
4. **Copy the whole block to the clipboard** with `pbcopy` so the user can paste it straight into their image provider.
5. Do **not** generate an image in this job, even if generation is available. Scan, hand back the block, stop.

If the user asks only for the empty template, return the template block — not a filled one.

## Job 2 — generate

Use when the user gives a prompt and asks for an image.

- Treat the user's text after `/aimg` as the generation prompt.
- Generate with the configured image provider/model.
- Copy the result into `~/Downloads` and reply with the final file path only.
- **Never fabricate.** No placeholder, mock, SVG, or PIL stand-in if generation fails. Report the real error concisely instead.
- No prompt supplied → ask for one.
- No generation tool available → say so and hand back the prompt block instead. That is still a complete answer.

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

## Rules

- **Scanning beats guessing.** If an image is on screen, read it. Never describe a photo from memory or imagination.
- **`CONSTRAINTS` is load-bearing**, not boilerplate — it's the line that keeps a stock image sellable.
- **Clipboard after every output** (macOS): `printf '%s' "<block or path>" | pbcopy`. For an image, copy the **path**, never the bytes. Skip silently on non-macOS; a clipboard failure must never fail the response.
- **Concise.** The block and the path, no commentary unless asked.
- Shell paths: use a fully expanded absolute path or `"$HOME/Downloads/..."`. Single-quoted `$HOME` does not expand.

## Output

Scan → the filled format block, on the clipboard.
Generate → the file path, on the clipboard.

```text
/Users/you/Downloads/your-image.png
```
