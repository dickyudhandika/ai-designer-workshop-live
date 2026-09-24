# Session 2 — Image Prompts for Placeholders

**15 minutes.** Turn every gray rectangle in the Figma homepage into a copy-pasteable, production-grade image prompt.

---

## What this session is

Session 1 ends with a homepage built from real tokens — nav, hero, grid, featured collection, footer — but every image slot is a placeholder: a `#F3F1EB` rectangle with "IMAGE PLACEHOLDER" written on it.

Session 2 makes those slots shippable. The agent reads the Figma file over MCP, finds each placeholder, reads its **context** (which section, how big, what text sits next to it), and writes a structured prompt that describes exactly the photo that belongs there.

No image generation required. The output is text — prompts the audience pastes into whatever provider they use (Midjourney, DALL·E, FAL, Ideogram, Firefly, a local model). That keeps the session fast, provider-neutral, and useful even for attendees whose agent has no image tool wired in.

---

## Agenda

| Min | Step | What happens |
|---|---|---|
| 0–2 | Context | Agent reads the Figma file, reports how many placeholders it found and where. |
| 2–5 | Template | Walk through `image-prompt-template.md` — the 8 sections and why each one exists. |
| 5–12 | Generate | Agent writes a prompt per placeholder. Audience watches the reasoning: hero vs. grid card vs. category thumbnail get different treatment. |
| 12–15 | Review | Read 2–3 prompts aloud. Ask: does this describe the photo you actually want in that slot? Iterate one. |

---

## The moment to land

A placeholder is a **design intent that was never written down**. The agent's job is to recover that intent from position, size, and surrounding copy — then make it explicit enough that an image model (or a photographer, or a stock search) can act on it.

The hero is 1200×600 — wide, editorial, sets the tone. The grid card is 400×300 — it is *inventory*, a photo the marketplace is "selling." A category thumbnail must be the category, legible at 160×120. Same template, three different readings of context.

---

## Files in this session

- `image-prompt-template.md` — the structured format. Extract from it, don't paraphrase it.
- `generate-prompts.md` — the agent prompt. This is what you hand the agent.

## Output

- `output/images/prompts.md` — one copy-pasteable block per placeholder, each labelled with its section and dimensions.

## Reference

- `examples/images/prompts-example.md` — what good output looks like: hero, grid card, featured collection, category thumbnail.

---

## Before you start

- Session 1 complete — the homepage frame exists in Figma with placeholders in it.
- The Figma MCP bridge is connected and `list_files` returns your file (see `setup/verify.md`).
- If the bridge is down, the agent can still run: ask it to read the placeholder list you paste in manually, or point it at `output/figma/` screenshots. Degrade, don't stall.
