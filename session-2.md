# Session 2 — Write the prompts that sell the images

**A guideline, not a script.** The agent executes; you drive.

Session 1 ended with a chosen variation: a real token system applied to a real design. It looks like a product.

It isn't one yet. Every image on it is a gray rectangle — and the brief promised a designer that these images look commissioned.

---

## What this session is

A placeholder is **a design intent that was never written down.** Right now the design says "an image goes here" and nothing more. Nobody can buy that.

This session turns each slot into a written prompt.

**We write prompts. We do not generate images.**

That's the whole point of the session — the prompt is the deliverable. Your agent writes the prompts and hands them to you; you take them to whatever image provider you already use: Midjourney, Nano Banana, DALL·E, FAL, Ideogram, Firefly, a local model.

The agent's job ends at the prompt. Two reasons:

- **Generation is your choice, not the agent's.** Model, style, credits, licence, resolution — those are decisions a person makes.
- **A good prompt travels.** It survives being pasted anywhere. A generated image is one output of it, and one you can always redo.

**Write for the brief, not for beauty.** The product's whole job is convincing a sceptic that these images are commissioned quality. Every prompt here has to earn that — an image that looks like free stock breaks the promise on the one screen that's supposed to sell it.

**Time:** ~15 min. Find placeholders · write prompts · collect · review.

---

## Step 1 — Find the placeholders

> Look at the variation we picked in Figma. Find every image placeholder in it.
>
> Tell me how many there are and where each one sits — which section, what size, and what text is next to it.

**The surrounding content is the brief.** If a card next to a slot reads "Misty pine forest — $12", that slot is a misty pine forest. The prompt follows the design, not your taste.

**What good looks like:** a count, and a location for each one. If the count is vague, the agent is guessing.

---

## Step 2 — Write a prompt per slot

**Four kinds of slot want four different prompts.** This is the part worth explaining to the room — a hero and a grid card are not the same brief.

| Slot | Read it as | The prompt leans toward |
|---|---|---|
| **Hero** | The tone-setter. Wide, dramatic. | Editorial, deep depth of field, room left for a headline |
| **Grid card** | *Inventory.* The photo being sold. | Commercial, one clear subject, readable at thumbnail size |
| **Collection** | A *curated set.* Cohesion beats any single frame. | Shared palette, shared light direction, same treatment across all of them |
| **Category thumbnail** | A label with a picture. | One unmistakable subject, legible when small |

**The grid is the product.** A buyer decides on the thumbnails — the hero sets the mood, but the grid is what they're actually paying for. If those prompts come back looking like the free tier, the screen fails.

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
> The product's job is convincing a sceptical designer that these images look commissioned. Write to that. Nothing here should read as stock filler.
>
> For the collection band and the category row, write them as one set: same light direction, same colour temperature, same camera treatment. A collection that looks like five different photographers isn't a collection.
>
> Write the prompts only. Do not generate any images. I'll take them to my own provider.

**Two rules that matter more than the rest:**

- **`[CONSTRAINTS]` is not boilerplate.** It's the line that stops the model putting signage on your architecture and a brand mark on your laptop. These are stock images — embedded text makes them unsellable.
- **Vary deliberately.** If two slots would naturally get the same subject, change season, time of day, or framing. A grid of five near-identical photos reads as one photo repeated.

**Reading a reference instead of inventing one.** If you already have a photo whose look you want, hand it to your agent and ask it to describe *that image* in the same eight sections. You get a prompt grounded in something real rather than a guess. With the `/aimg` skill installed (see `setup/aimg.md`) it's a single step — scan the image, return the filled block.

**What good looks like:** every prompt is self-contained. Paste it into any provider with zero edits and it means something.

---

## Step 3 — Collect the prompts

> Put every prompt in one place: `prompts.md` at the repo root. Name each one after its slot — hero, card-1, collection, category-travel — and say which section of the design it belongs to.
>
> Return the full set as a single copy-paste block too, so I can grab it without opening the file.

One file, one block. The file is the record; the block is for grabbing on stage.

**Nothing gets generated here.** If your agent offers to make the images, say no — you're taking the prompts to your own provider afterward. If it produces an image anyway, that's a deviation worth naming out loud.

**What good looks like:** N placeholders in, N named prompts out, all eight sections each.

---

## Step 4 — Review the set

> Read the prompts back to me as a set. Do they look like one product, or like eight unrelated photos?

Three questions for the room:

1. **Do these hold together** — or does the set read like five different photographers?
2. **Could a designer tell these from free stock?** If not, they won't support a higher price — that's the commercial test, and it's the hardest one here.
3. **Would anything fight the tokens** when the image lands — a photo that makes text unreadable, a colour that clashes with the one accent?

Fix one prompt together, on screen. Cheapest possible place to catch a bad brief — before anyone spends a credit on it.

**What good looks like:** at least one prompt still isn't right, and you both know why.

---

## Done when

- Every placeholder in the chosen frame has a prompt in `prompts.md`
- Every prompt has all eight sections, in order
- Prompts are self-contained — pasteable into any provider with no edits
- Collection and category slots were written as coherent sets, not one-offs
- **No images were generated** — the deliverable is the prompt set
- You've named at least one prompt that still isn't right
- The prompts read as imagery a designer would pay for, not as free stock

---

## Where this goes next

Take the prompts to your provider of choice and see the gray boxes become photographs. That part is yours, not the agent's.

Then the brief closes: a designer lands on this screen, stops believing AI stock looks cheap, and pays. That's the whole product, and you built it from evidence, four directions, one decision, and a token system.

The same loop on a real project: research with evidence, several rough directions, one choice, tokens assigned, then real content. The AI photostock was a worked example — the shape of the workflow is the product.

What made it work wasn't the agent's taste. It was `assets/DESIGN.md` — a contract short enough for a human to read and precise enough for an agent to execute, with a token system that makes its own mistakes measurable.
