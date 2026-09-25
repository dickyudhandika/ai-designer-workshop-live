# `/aimg` — image generation shortcut

Optional. Session 2 works without it — the prompt format is the deliverable either way. This is the convenience layer for actually generating.

---

## What it is

`/aimg` is a **Hermes skill**: you invoke it with a prompt, it generates an image, and it replies with the file path so you can drop that image straight into a Figma frame.

```
/aimg Editorial landscape photography. A dramatic mountain range at golden hour...
→ /Users/you/Downloads/mountain-range.png
```

Two behaviours worth knowing:

- It **copies the newest generated image to `~/Downloads`** and returns that path — no hunting through a cache directory.
- It **refuses to fabricate.** If the provider fails, it reports the real error instead of handing you a placeholder. That matters in a live session: a named failure is worth more than a fake success.

---

## Install (Hermes)

The skill ships with this Hermes setup at `~/.hermes/skills/devops/aimg/`. Check it's there:

```bash
ls ~/.hermes/skills/devops/aimg/SKILL.md
```

If it's missing, it isn't in any public registry (`hermes skills search aimg` returns nothing), so create it from the definition below rather than looking for a package to install.

Requires a configured image provider — `/aimg` uses whatever `image_gen` is set to in your Hermes config:

```bash
hermes config get image_gen
```

If that's empty, image generation has nowhere to go. Set a provider, or use Session 2 Option B and export the prompts instead.

---

## Other agents (Claude Code, Cursor, Codex, Windsurf)

**There is no `/aimg` to install.** It's a Hermes skill — a slash command tied to Hermes's skill system, and it isn't published anywhere else.

Two things you can do instead:

1. **Skip it.** Session 2 Option B: have your agent export the prompts to `output/images/prompts.md` and paste them into Midjourney, Nano Banana, DALL·E, FAL, or whatever you use. The eight-section format is provider-neutral on purpose.
2. **Ask your agent to create an equivalent.** Paste the definition below and say: *"create this as a skill in your skills folder."* Every agent that supports skills can hold it; only the invocation syntax differs.

The **format** is the portable asset. `/aimg` is one way to run it.

---

## Skill definition

Give this to your agent if you want the equivalent.

```markdown
---
name: aimg
description: Generate an image from the user's prompt and deliver the newest result path in a copy-paste friendly way.
tags:
  - image-generation
  - shortcut
---

# aimg

Use this skill when the user invokes `/aimg`.

## Goal

Generate an image from the user's prompt, copy the newest generated image to
`~/Downloads`, and reply with the final file path only.

## Rules

- Treat the user's text after `/aimg` as the generation prompt.
- Be concise. No extra commentary unless asked.
- If the user gave no prompt, ask for one.
- Use the configured image generation provider/model. Do NOT create local
  placeholder, mock, SVG, or PIL fallback images if provider generation fails.
- If generation fails, report the real error concisely instead of returning a
  fabricated image path.
- When copying in shell, use a fully expanded absolute path or a double-quoted
  "$HOME/Downloads/...". Single-quoted $HOME does not expand.
- After output, on macOS, copy the absolute file path with pbcopy so the user can
  paste it straight into another app. Skip silently if pbcopy is unavailable.
```

---

## The prompt format it consumes

`/aimg` takes any prompt. The format Session 2 uses is an **image-analysis** template as much as a generation one — the same eight sections describe a photo you already have.

```text
[PHOTOGRAPHY TYPE & SUBJECT] :
Identify the photography genre and clearly describe the exact subject.
Include the photography type (Commercial, Editorial, Product, Lifestyle, Beauty)
and reference the subject.

[SUBJECT ACTION] (subject position)
How the subject is positioned or what it is doing, to avoid a floating look
(standing, leaning, lying, floating, angled).

[ENVIRONMENT] –
The setting and background, including the surface or base.

[LIGHTING] (direction, type, mood, shadows)
Direction (front, side, back, top), type (natural, studio, softbox, neon), mood,
and shadow quality.

[CAMERA] (angle, lens feel, depth of field, focus)
Angle, depth of field (shallow or deep), and focus (sharp subject, blurred
background).

[TEXTURE & PROPS] (materials, surface details, added elements)
Visible textures, materials, environmental effects, supporting props.

[STYLE KEYWORDS]
Short descriptive keywords summarising the aesthetic.

[CONSTRAINTS]
Strict rules to preserve the original subject — no logo changes, no text edits,
no shape distortion.
```

Useful for Session 2 either way: point it at a reference image and it produces a reusable prompt, not just a one-off generation.
