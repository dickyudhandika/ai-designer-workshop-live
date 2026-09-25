# `/aimg` — the image-prompt skill

Optional, and installable on **any agent** — Codex, Claude Code, Cursor, Windsurf, Hermes.

Session 2 works without it. But with it, your agent can take a reference image and hand you back a reusable eight-section prompt on the clipboard, or generate the images itself.

---

## What it is

A plain **`SKILL.md`** — the Agent Skills format. No build step, no package to install. It ships in this repo at [`skills/aimg/SKILL.md`](../skills/aimg/SKILL.md).

Two jobs:

| Job | You do this | You get back |
|---|---|---|
| **Scan** | Attach a reference image, say *"scan this into a prompt"* | The filled eight-section format, on your clipboard |
| **Generate** | Give it a prompt | The image at `~/Downloads`, path on your clipboard |

**The scan job is the useful one.** A reference photo in, a prompt you can reuse out — that's the format travelling, not just an image.

Two behaviours worth knowing:

- It **copies the newest generated image to `~/Downloads`** and returns that path — no hunting through a cache directory.
- It **refuses to fabricate.** No placeholder, mock, SVG, or PIL stand-in. If the provider fails, it reports the real error instead of handing you a fake. That matters in a live session: a named failure beats a fake success.

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

**Hermes** keeps its skills at `~/.hermes/skills/devops/aimg/` and invokes `/aimg` as a slash command.

Then **restart the agent** so it picks the skill up.

### Requirements for the generate job

The scan job needs nothing but vision. Generation needs a configured image provider.

Hermes:

```bash
hermes config get image_gen
```

Empty → generation has nowhere to go. Scan still works; use Session 2 Option B and paste the prompts into your own provider.

---

## The prompt format it uses

Eight sections, in this order. The same template works for **analysis and generation** — which is why it's worth keeping.

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

**Provider-neutral on purpose.** The output is text, so it pastes into Midjourney, Nano Banana, DALL·E, FAL, Ideogram, Firefly, or a local model with zero edits.

---

## If you'd rather not install anything

Paste the skill body into your agent's context and say *"follow this when I hand you an image."* It's markdown — that's the whole skill.

Or skip it entirely: ask your agent to write the prompts and export them to `output/images/prompts.md`. That's Session 2 Option B, and it's a complete result.
