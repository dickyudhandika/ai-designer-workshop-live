# Session 1 — Build an AI photostock for designers

**You drive this. Your agent executes.** Read a step, then give your agent the prompt in it.

Setup must be done first — `AGENTS.md`, and the six checks passing.

---

## The case study

You're building an **AI photostock for designers** — a mobile product where designers browse, search and buy AI-generated imagery. It's framed as the polished case study you'd want for your next project: a real product, real research, real tokens, not a dribbble shot.

The whole session hangs on one idea: **a design system is a contract, and you can watch an agent execute it against a real design tool.** You'll see that happen at step 6.

**Time:** ~45 min. Rough budget: 10 research · 5 references · 10 lo-fi · 5 pick · 10 tokens · 5 inspect.

---

## Step 1 — Frame the case study (2 min)

Tell your agent what's being built and what it's for. This context steers every later decision, so say it out loud rather than assuming.

> We're designing an AI photostock product for designers — a mobile app where you browse, search and buy AI-generated images. Treat it as a portfolio-grade case study. Everything we build today goes in one Figma file.

---

## Step 2 — Research the layouts with Mobbin (10 min)

Mobile, not desktop. The product is a phone app, so the evidence has to be phone evidence.

**Mobbin is the source** — `search_screens`. Two rules decide whether a query works:

- Describe **one screen** in plain language, not a keyword list. `"marketplace app home screen with photo grid and search bar"` works. `"photo marketplace stock"` returns nothing.
- **Never put the platform inside the query.** `platform` is a separate parameter — `"photo app ios"` degrades the match.

> Use Mobbin MCP. Search screens with: `marketplace app home screen with photo grid and search bar`, platform `ios`, limit 12.
>
> I want home screens whose whole job is showing a searchable grid of photographs.
>
> Then tell me which apps came back, and for each one what its home screen does — where the search sits, how many grid columns, what's in the bottom bar.

**Expect this query to return Depop, Etsy, Vinted, Vestiaire Collective, Nextdoor, eBay and similar — image-grid marketplaces, not photo stock apps.**

That gap is real and worth saying to the room: stock-photo apps barely exist on Mobbin, while image-grid marketplaces are everywhere. Both are solving the same design problem — a mobile screen that shows a searchable grid of photos. Study the ones with evidence; build the photostock.

**If a query returns `[]`,** try at most two variations, then drop that candidate and move on. Name what you dropped. Never describe a screen from memory.

---

## Step 3 — Pick 1–3 you love, with reasons (5 min)

Not a shortlist of five. **One to three** you actually want to build on — and be able to say why.

> From those, I want to pick the ones I actually love. Show me your top 3 with a reason each — what it does with search, its grid, and anything mobile-specific worth stealing.
>
> Then recommend one as the base.

Say your reason out loud in the room. "I like it" isn't a reason. "Search is the widest thing on screen and the grid starts immediately" is.

**Then pick.** You can override the agent's recommendation — that's your call, and the session continues with your pick. Have the agent record your choice.

---

## Step 4 — Merge them and go lo-fi (10 min)

Don't clone one reference. Merge the best decisions from your picks into a direction of your own.

**Lo-fi means structure, not beauty.** Boxes, labels, gray rectangles. No real images, no polishing. Fast and disposable — the point is to see several shapes of the same idea.

**1 to 4 variations is the right range.** Fewer than two and you haven't explored; more than four and you're burning time on directions nobody will pick.

> Now merge the best of those into an AI photostock mobile homepage. Give me 4 quick lo-fi variations — structure only, grays and boxes, no images, no polish.
>
> Make each one a genuinely different answer to "how does a designer find an image here". Name them A, B, C, D and put them side by side so I can compare.

**Frame them at 390px wide** — phone width — and hold that width across all of them so they're comparable.

Things worth varying between versions: where search sits, whether the grid is 1 or 2 columns, what's in the bottom bar, whether there's a hero at all.

---

## Step 5 — Pick the best one (5 min)

Look at the four together. Pick one, and say why it won.

> I'm picking [X]. Tell me why it's the strongest of the four, and what you'd fix in it.

Have your agent record the pick. Everything after this happens to the chosen frame only.

---

## Step 6 — Assign your design tokens (10 min)

**This is the moment the session is built around.**

`assets/DESIGN.md` is the token source. Read it — it's plain YAML anyone in the room can open. The agent turns it into **real Figma variables and text styles**, live, while you talk.

> Read `assets/DESIGN.md`. Create the tokens in Figma as real variable collections and text styles — colors, spacing, radius, typography.
>
> Then apply them to the variation I picked: every fill, border, padding, radius and type size resolves from a token, not a hardcoded number.
>
> Tell me the exact counts when you're done.

**Ask the room to look at their own Figma sidebar while this runs.** Names appear — `color/background`, `color/primary`, then the text styles. That sidebar is the proof: a DESIGN.md is a contract and this is an agent executing it against a real design tool.

Two things worth narrating:

- **The tokens are the same file the room can read.** Nothing is hidden in the agent's memory. `assets/DESIGN.md` is the source of truth and anyone can edit it.
- **The conversion is real work.** `lineHeight: 1.17` becomes `117 PERCENT`; `letterSpacing: -0.01em` at 48px becomes `-0.48`. The agent does that arithmetic for every typography token. Tedious precision is what agents are actually good at.

**If a font fails to load** — "Fauna One could not be loaded" is expected — have it fall back to **Playfair Display** for serif titles.

---

## Step 7 — Inspect what the tokens did (5 min)

The honest step, and the one that makes the rest credible.

Two things to look for:

1. **What the tokens improved** — consistency, spacing rhythm, one clear accent instead of five near-identical grays.
2. **What they broke or exposed** — and there's usually something. A contrast value that fails, a radius that doesn't fit, a rule in the file that contradicts the frame.

> Now audit what you built against `assets/DESIGN.md`. Where does it follow the tokens, and where did the tokens cause a problem?
>
> Check the contrast of every text colour against its background and give me the measured ratios. If anything fails, say so — don't quietly change it.

**Expect a real finding here.** On a live run of this exact flow, the audit measured `#A1A1A1` at **2.52:1** against the warm-white canvas — below the 4.5:1 the design file itself claims it passes. 15 text nodes were affected. The agent had followed the file exactly and the file was wrong.

That's the lesson to land: **the token system makes the mistake visible.** Before tokens, a bad gray is one hardcoded value among hundreds and nobody notices. After tokens, it's one number in one place that the whole design inherits — and it can be measured.

Ask: *should we fix the token, or the rule?*

---

## Between steps

**Pause after each one.** Show the room the artifact, let them react, take the next decision together. The pauses are where the workshop actually happens — racing through all seven steps in silence is a demo, not a workshop.

---

## If something breaks

| Problem | What to do |
|---|---|
| Mobbin returns `[]` for everything | Write the report from whatever you can verify; draw wireframes for the rest and label them `wireframe — capture unavailable`. Say so out loud. Never describe a screen from memory. |
| Figma bridge unreachable | Re-run the checks in `AGENTS.md`. It fails silently more often than loudly. |
| A font won't load | Playfair Display for serif titles |
| Agent reports success but Figma looks wrong | Ask it to re-read the node and report the actual bounds. Silent failures are common; a claim of success isn't evidence. |

---

## Done when

- A chosen variation exists in Figma at 390px wide
- Its colours, spacing, radius and type all resolve from Figma variables and text styles
- `assets/DESIGN.md` is the stated source of those tokens
- The room has seen the variables appear live in Figma's sidebar
- You've named at least one thing the tokens improved **and** one thing they broke
- The chosen variation is on screen, ready for `session-2.md`
