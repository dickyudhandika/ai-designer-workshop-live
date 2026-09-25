# Session 2 — Make it sellable

**You drive this. Your agent executes.**

Session 1 ended with a chosen variation: a real token system applied to a real design. It looks like a product.

It isn't one yet. Every image on it is a gray rectangle.

---

## What this session is

A placeholder is **a design intent that was never written down.** Right now the design says "an image goes here" and nothing more. Nobody can buy that.

This session makes the slots real. The agent reads the chosen frame, finds every image placeholder, works out what belongs in each one from its position, size and surrounding copy — then writes a prompt per slot, and the images go in.

**Time:** ~15 min. Find placeholders · write prompts · generate · place.

**No image provider is required.** If your agent can generate images, it places them. If it can't, the prompts are still the deliverable — copy-pasteable into Midjourney, DALL·E, FAL, Ideogram, Firefly, whatever you use.

---

## Step 1 — Find the placeholders (2 min)

> Look at the variation we picked in Figma. Find every image placeholder in it.
>
> Tell me how many there are and where each one sits — which section, what size, and what text is next to it.

**The count matters.** If two placeholders sit next to "Misty pine forest — $12", that slot is that photo, not a beach. The prompt follows the design, not your taste.

---

## Step 2 — Write a prompt per slot (5 min)

**Four kinds of slot, four different prompts.** This is the part worth explaining to the room — a hero and a grid card want completely different images.

| Slot | Read it as | The prompt leans toward |
|---|---|---|
| **Hero** | The tone-setter. Wide, dramatic. | Editorial, deep depth of field, room left for a headline |
| **Grid card** | *Inventory.* The photo being sold. | Commercial, one clear subject, reads at thumbnail size |
| **Collection** | A *curated set.* Cohesion matters more than any single frame. | Shared palette, shared light direction, same treatment across all of them |
| **Category thumbnail** | A label with a picture. | One unmistakable subject, legible when small |

Use this eight-section structure per prompt. Every section earns its place — drop one and the model guesses.

```text
[PHOTOGRAPHY TYPE & SUBJECT] :
Genre and the exact subject.

[SUBJECT ACTION] (subject position)
How it sits in space — standing, leaning, resting. Stops it floating.

[ENVIRONMENT] –
The setting and background.

[LIGHTING] (direction, type, mood, shadows)
Where the light comes from and what it does.

[CAMERA] (angle, lens feel, depth of field, focus)
Perspective and sharpness.

[TEXTURE & PROPS] (materials, surface details, added elements)
Materials and what else is in frame.

[STYLE KEYWORDS]
4–7 comma-separated terms.

[CONSTRAINTS]
No text. No logos. No watermarks.
```

> For each placeholder, write a prompt using these eight sections in this order. Ground each one in what's actually next to the slot in the design — the card title, the category name.
>
> For the collection band and the category row, write them as one set: same light direction, same colour temperature, same camera treatment. A collection that looks like five different photographers isn't a collection.

**The `[CONSTRAINTS]` line is not boilerplate.** It's the line that stops the model putting signage on your architecture and a brand mark on your laptop. These are stock images — embedded text makes them unsellable.

---

## Step 3 — Generate and place (5 min)

> Now generate each image and place it into its placeholder in Figma. Keep the slot dimensions exactly — don't crop to fit, and don't change the layout.

If your agent has no image tool:

> Skip generation — export the prompts to `output/images/prompts.md` so I can paste them into my own provider.

**Ask the room to watch the gray boxes disappear.** That's the payoff of the whole workshop: the same frame they watched get researched, structured and tokenized is now a product with photographs in it.

---

## Step 4 — Look at it as a buyer (3 min)

> Screenshot the finished frame and tell me: does this look like something you'd pay for?

Three questions worth asking the room:

1. **Do the images hold together** — or does it look like five different photographers?
2. **Does anything fight the tokens** — an image that makes the text unreadable, a colour that clashes with the one accent?
3. **Is the product obvious** — can a designer tell what they'd be buying from a first glance?

Anything broken here is a real finding. Fix one thing, together, on screen.

---

## Done when

- Every placeholder in the chosen frame is either filled with an image or has a prompt in `output/images/prompts.md`
- Prompts follow the eight-section structure, in order
- The collection and category slots were written as coherent sets, not one-offs
- The room has seen the frame go from gray boxes to photographs
- You've named at least one thing that still doesn't work

---

## Where this goes next

The same loop, on a real project: research with evidence, several rough directions, one choice, tokens assigned, then real content. The AI photostock was a case study — but the shape of the workflow is the product.

The thing that made it work wasn't the agent's taste. It was `assets/DESIGN.md` — a contract small enough for a human to read and precise enough for an agent to execute, with a token system that makes its own mistakes measurable.
