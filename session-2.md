# Session 2 — Make it sellable

**A guideline, not a script.** The agent executes; you drive.

Session 1 ended with a chosen variation: a real token system applied to a real design. It looks like a product.

It isn't one yet. Every image on it is a gray rectangle.

---

## What this session is

A placeholder is **a design intent that was never written down.** Right now the design says "an image goes here" and nothing more. Nobody can buy that.

This session turns each slot into a written prompt — then, if your tooling allows, into an image.

**The prompt format is the deliverable, not the image.** Any image provider can consume it: Midjourney, Nano Banana, DALL·E, FAL, Ideogram, Firefly, a local model. A good prompt survives being pasted anywhere; a generated image is one output of it.

**Time:** ~15 min. Find placeholders · write prompts · generate or export · review.

---

## Step 1 — Find the placeholders

> Look at the variation we picked in Figma. Find every image placeholder in it.
>
> Tell me how many there are and where each one sits — which section, what size, and what text is next to it.

**The surrounding content is the brief.** If a card next to a slot reads "Misty pine forest — $12", that slot is a misty pine forest. The prompt follows the design, not your taste.

**What good looks like:** a count, and a location for each one. If the count is vague, the agent is guessing.

---

## Step 2 — Write a prompt per slot

**Four kinds of slot want four different images.** This is the part worth explaining to the room — a hero and a grid card are not the same brief.

| Slot | Read it as | The prompt leans toward |
|---|---|---|
| **Hero** | The tone-setter. Wide, dramatic. | Editorial, deep depth of field, room left for a headline |
| **Grid card** | *Inventory.* The photo being sold. | Commercial, one clear subject, readable at thumbnail size |
| **Collection** | A *curated set.* Cohesion beats any single frame. | Shared palette, shared light direction, same treatment across all of them |
| **Category thumbnail** | A label with a picture. | One unmistakable subject, legible when small |

### The format

Eight sections, in this order. Each one answers a question the model would otherwise guess at.

```text
[PHOTOGRAPHY TYPE & SUBJECT] :
Genre and the exact subject. Commercial, Editorial, Product, Lifestyle, Beauty.

[SUBJECT ACTION] (subject position)
How it sits in space — standing, leaning, resting, angled. Stops it floating.

[ENVIRONMENT] –
The setting and background, including the surface or base.

[LIGHTING] (direction, type, mood, shadows)
Direction (front, side, back, top), type (natural, studio, softbox, neon), mood, shadow quality.

[CAMERA] (angle, lens feel, depth of field, focus)
Angle, shallow or deep focus, what's sharp and what isn't.

[TEXTURE & PROPS] (materials, surface details, added elements)
Visible textures, materials, environmental effects, supporting props.

[STYLE KEYWORDS]
4–7 comma-separated terms.

[CONSTRAINTS]
No text. No logos. No watermarks. No shape distortion.
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

> For each placeholder, write a prompt using these eight sections in this order. Ground each one in what's actually next to the slot — the card title, the category name.
>
> For the collection band and the category row, write them as one set: same light direction, same colour temperature, same camera treatment. A collection that looks like five different photographers isn't a collection.

**Two rules that matter more than the rest:**

- **`[CONSTRAINTS]` is not boilerplate.** It's the line that stops the model putting signage on your architecture and a brand mark on your laptop. These are stock images — embedded text makes them unsellable.
- **Vary deliberately.** If two slots would naturally get the same subject, change season, time of day, or framing. A grid of five near-identical photos reads as one photo repeated.

**Why this format travels:** it's an **image-analysis** template as much as a generation one. The same eight sections describe a photo you already have — so the room can point it at a reference image and get a reusable prompt out, not just a one-off.

**What good looks like:** every prompt is self-contained. Paste it into any provider with zero edits and it means something.

---

## Step 3 — Generate — or export

**Pick whichever fits your tooling. Both are a success.**

### Option A — your agent has an image tool

> Generate each image and place it into its placeholder in Figma. Keep the slot dimensions exactly — don't crop to fit, and don't change the layout.

**Hermes users:** the `/aimg` skill does this — invoke it with the prompt and it returns the generated image path for you to drop into the frame. See `setup/aimg.md`.

### Option B — no image tool

> Export the prompts to `output/images/prompts.md` so I can paste them into my own provider.

Copy-pasteable prompts are the full deliverable. Take them to Midjourney, Nano Banana, DALL·E, FAL, Ideogram, Firefly, whatever you use — the format is provider-neutral on purpose.

**Do this live if you can.** Watching gray boxes turn into photographs is the payoff of the whole workshop: the same frame the room watched get researched, structured and tokenized is now a product.

**If generation fails,** say so and export the prompts. Do not accept a placeholder image, a mock, or an SVG stand-in passed off as a generation — a named failure is worth more than a fake success.

---

## Step 4 — Look at it as a buyer

> Screenshot the finished frame and tell me: does this look like something you'd pay for?

Three questions for the room:

1. **Do the images hold together** — or does it look like five different photographers?
2. **Does anything fight the tokens** — an image that makes text unreadable, a colour that clashes with the one accent?
3. **Is the product obvious** — can a designer tell what they'd be buying at a glance?

Anything broken here is a real finding. Fix one thing together, on screen.

**What good looks like:** at least one thing still doesn't work, and you both know why.

---

## Done when

- Every placeholder in the chosen frame is either filled with an image, or has a prompt in `output/images/prompts.md`
- Every prompt has all eight sections, in order
- Prompts are self-contained — pasteable into any provider with no edits
- Collection and category slots were written as coherent sets, not one-offs
- The room has seen the frame go from gray boxes to photographs (or knows exactly why not)
- You've named at least one thing that still doesn't work

---

## Where this goes next

The same loop on a real project: research with evidence, several rough directions, one choice, tokens assigned, then real content. The AI photostock was a case study — the shape of the workflow is the product.

What made it work wasn't the agent's taste. It was `assets/DESIGN.md` — a contract short enough for a human to read and precise enough for an agent to execute, with a token system that makes its own mistakes measurable.
