# `/aimg` — the image-prompt skill

**Optional tier.** Not required for Session 1, and Session 2 works without it.

Installable on **any agent** — Codex, Claude Code, Cursor, Windsurf, Hermes.

It turns a reference image into a reusable eight-section prompt, and puts the block on your clipboard.

**It does not generate images.** That's deliberate — see below.

Verification for this tier lives in `verify.md` under **Optional**.

---

## What it is

A plain **`SKILL.md`** — the Agent Skills format. No build step, no package to install. It ships in this repo at [`skills/aimg/SKILL.md`](../skills/aimg/SKILL.md).

Three steps, and then it stops:

1. **Look at the image** — read the actual pixels, not a remembered description.
2. **Scan it** against the eight sections, in order.
3. **Copy the whole filled block to the clipboard** (`pbcopy`), ready to paste into your provider.

No generation step. Not a placeholder, not a mock, not an SVG stand-in.

---

## Why prompts and not images

Because the prompt is the asset and generation is your call.

- **Generation is a decision, not a task.** Model, style, credits, licence, resolution, how many attempts. A person makes those calls.
- **A prompt travels; an image doesn't.** The same block works in Midjourney, Nano Banana, DALL·E, FAL, Ideogram, Firefly, or a local model. Change provider tomorrow and the prompt still holds.
- **Prompts are reviewable before they cost anything.** Best place to catch a bad brief is before someone spends credits on it.

The format is one template used two ways: describe an image you already have, or specify one you want. Same eight sections either way.

---

## Install

From the repo root:

```bash
mkdir -p ~/.agents/skills && cp -R "$(pwd)/skills/aimg" ~/.agents/skills/aimg
```

**`~/.agents/skills/` is the cross-agent convention** — Codex, Cursor, Gemini CLI and most skill loaders read it directly.

Some agents only scan their own folder. Symlink it across instead — one copy stays the source of truth, and Claude Code and Cursor both follow symlinks:

```bash
ln -sfn ~/.agents/skills/aimg ~/.claude/skills/aimg    # Claude Code
ln -sfn ~/.agents/skills/aimg ~/.cursor/skills/aimg    # Cursor
ln -sfn ~/.agents/skills/aimg ~/.codex/skills/aimg     # Codex
```

**Hermes** keeps its skills at `~/.hermes/skills/devops/aimg/`.

Then **restart the agent** so it picks the skill up.

No image provider needed. The scan job is vision only — nothing to configure.

### Verify it

```bash
ls -la ~/.agents/skills/aimg/SKILL.md
```

Then ask your agent: *"do you have the aimg skill, and what does it do?"* It should find the skill and describe scanning an image into the eight-section format.

Not found → the agent restarted before the file landed, or it reads only its own folder. Re-check the paths above and restart. Full check list: `verify.md`.

---

## The prompt format it uses

Eight sections, in this order. The same template works for **analysis and specification** — which is why it's worth keeping.

```text
[PHOTOGRAPHY TYPE & SUBJECT] :
Identify the photography genre and clearly describe the exact subject.
Include the photography type (Commercial, Editorial, Product, Lifestyle, Beauty)
and reference the actual subject.

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
Strict rules to preserve the subject and keep it usable (no text, no logos, no
watermarks, no shape distortion). Keep the subject exactly as shown.
```

Each section answers a question the model would otherwise guess at:

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

**Provider-neutral on purpose.** The output is text, so it pastes anywhere with zero edits.

---

## If you'd rather not install anything

Paste the skill body into your agent's context and say *"follow this when I hand you an image."* It's markdown — that's the whole skill.

Or skip it entirely: ask your agent to write the prompts per slot and collect them in `prompts.md`. That's Session 2 without the skill, and it's a complete result.
