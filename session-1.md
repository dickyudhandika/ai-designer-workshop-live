# Session 1 — Build an AI photostock for designers

**A guideline, not a script.** Your agent executes; you drive. The steps are in order, the prompts are starting points — adapt them to what your agent actually gives back and to the room's mood.

Setup first: `AGENTS.md`, six checks passing.

---

## The case study

You're building an **AI photostock for designers** — a mobile product where designers browse, search and buy AI-generated imagery. Frame it as the polished case study you'd want for your next project: real research, several directions, one choice, a real token system.

It's a worked example. Swap the product if a different one fits your room better — what matters is that it's an **image grid you can search**, because that's what the whole session is shaped around.

**One idea holds the session together:** a design system is a contract, and you can watch an agent execute it against a real design tool. That happens at step 6.

**Time:** ~45 min, adjustable. Research · pick references · lo-fi · choose · tokens · inspect.

---

## Step 1 — Frame the case study

Before anything is researched, say what's being built and what it's for. This context steers every later decision, so it's worth a sentence out loud rather than an assumption.

> We're designing an AI photostock for designers — a mobile app where you browse, search and buy AI-generated images. Treat it as a portfolio-grade case study. Everything we build today goes in one Figma file.

**What good looks like:** the agent can state back what the product is and who it's for. If it can't, the brief was too thin.

---

## Step 2 — Research the layouts

Mobile, not desktop — the product is a phone app, so the evidence has to be phone evidence.

**Mobbin is the source.** Three rules decide whether a query returns anything:

- **Describe one screen in plain language.** `"marketplace app home screen with photo grid and search bar"` works. A keyword pile like `"photo marketplace stock"` returns nothing.
- **Keep the platform out of the query.** `platform` is a separate parameter — putting `ios` in the text degrades the match.
- **One screen at a time.** Flows and multi-screen queries belong to `search_flows`, not here.

> Search Mobbin for home screens whose whole job is showing a searchable grid of photographs. Start with something like: `marketplace app home screen with photo grid and search bar`, platform `ios`, limit 12.
>
> Then tell me which apps came back, and for each one what its home screen does — where the search sits, how many grid columns, what's in the bottom bar.

**Adapt the query to your product.** The structure above — *screen type + the thing it does + what's on it* — is the part that transfers. If you're building something else, describe it the same way.

**A real finding from this exact search, worth saying to the room:** stock-photo apps barely exist on Mobbin, while image-grid marketplaces are everywhere. Both solve the same design problem — a mobile screen that shows a searchable grid of photos. Study what has evidence, build what you actually want. That's a research skill, not a workaround.

**If a query returns `[]`,** try at most two variations, then drop it and move on. Name what you dropped. Never describe a screen from memory.

**What good looks like:** several named apps, each with a specific observation about its home screen. Not a list of logos.

---

## Step 3 — Pick 1–3 you love, with reasons

Not a shortlist of five. **One to three** you actually want to build on — and be able to say why.

> From those, show me your top 3, with a reason each — what it does with search, its grid, and anything mobile-specific worth stealing. Then recommend one as the base.

**A reason is a design decision, not a feeling.** "I like it" isn't one. "Search is the widest thing on screen and the grid starts immediately" is.

**You pick, not the agent.** It recommends; you decide. Record your choice — everything after this inherits it.

**What good looks like:** you can explain your pick to the room in one sentence without repeating the agent's words.

---

## Step 4 — Merge and go lo-fi

Don't clone one reference. Merge the best decisions from your picks into a direction of your own.

**Lo-fi means structure, not beauty.** Boxes, labels, gray rectangles. No real images, no polish. Fast and disposable — the point is to see several shapes of the same idea before committing to one.

**Two to four variations is the useful range.** One isn't exploring. Past four you're burning time on directions nobody will pick.

> Merge the best of those into an AI photostock mobile homepage. Give me 4 quick lo-fi variations — structure only, grays and boxes, no images, no polish.
>
> Make each a genuinely different answer to "how does a designer find an image here". Name them A–D and put them side by side so I can compare.

**Hold one frame width across all of them** — phone width, 390px — so they're actually comparable.

Worth varying: where search sits, one column vs two, what's in the bottom bar, whether there's a hero at all. If two variations differ only in spacing, you've made one variation twice.

**What good looks like:** four frames that would fail differently. You can say in one line what each is betting on.

---

## Step 5 — Pick the best one

Look at them together. Pick one, and say why it won.

> I'm picking [X]. Tell me why it's the strongest of the four, and what you'd fix in it.

Everything after this happens to that frame only.

**What good looks like:** a pick you can defend, and a short list of things you know are wrong with it. The flaws are useful — step 7 will surface them again.

---

## Step 6 — Assign your design tokens

**The moment the session is built around.**

`assets/DESIGN.md` is the token source — plain YAML anyone in the room can open. The agent turns it into **real Figma variables and text styles**, live, while you talk.

> Read `assets/DESIGN.md`. Create the tokens in Figma as real variable collections and text styles — colors, spacing, radius, typography.
>
> Then apply them to the variation I picked: every fill, border, padding, radius and type size resolves from a token, not a hardcoded number.
>
> Tell me the exact counts when you're done.

**Ask the room to watch their own Figma sidebar while this runs.** Names appear — `color/background`, `color/primary`, then the text styles. That sidebar is the proof: a DESIGN.md is a contract, and this is an agent executing it against a real design tool.

Three things worth narrating:

- **The tokens are the same file the room can read.** Nothing is hidden in the agent's memory. `assets/DESIGN.md` is the source of truth and anyone can edit it.
- **The conversion is real work.** `lineHeight: 1.17` becomes `117 PERCENT`; `letterSpacing: -0.01em` at 48px becomes `-0.48`. That arithmetic happens for every typography token. Tedious precision is what agents are actually good at.
- **Counts are evidence.** The agent's numbers should match what's in the file — a mismatch is worth catching live, because it usually means something silently failed.

**If a font won't load** — "Fauna One could not be loaded" is a common one — fall back to a serif you do have, like Playfair Display.

**What good looks like:** the sidebar fills with named tokens, the frame repaints from them, and the counts match the file.

---

## Step 7 — Inspect what the tokens did

The honest step, and the one that makes the rest credible.

Two things to look for:

1. **What the tokens improved** — consistency, spacing rhythm, one clear accent instead of five near-identical grays.
2. **What they broke or exposed** — and something usually does. A contrast value that fails. A radius that fights the reference. A rule in the file that contradicts the frame you built.

> Audit what you built against `assets/DESIGN.md`. Where does it follow the tokens, and where did the tokens cause a problem?
>
> Check the contrast of every text colour against its background and give me the measured ratios. If something fails, say so — don't quietly change it.

**Ask for measurements, not opinions.** "Muted grey fails AA" is a claim. "`#A1A1A1` on `#FDFCF8` measures 2.52:1, needs 4.5:1" is evidence. The second one is the entire point of having tokens.

**The class of finding to watch for:** the agent followed the file exactly, and the file was wrong. A live run of this flow measured a secondary grey at **2.52:1** against the warm-white canvas — well under the 4.5:1 the design file itself claimed it passed, across 15 text nodes. Nobody had noticed, because before tokens a bad grey is one hardcoded value among hundreds. After tokens it's one number in one place, inherited everywhere, and measurable.

If you find something like that, it's the lesson to land: **the token system doesn't make the design good, it makes the mistakes visible.** Then ask the room: fix the token, or fix the rule?

**What good looks like:** at least one thing named as improved and one thing named as broken or exposed — with a number attached to the second.

---

## Between steps

**Pause after each one.** Show the room the artifact, let them react, take the next decision together. The pauses are where the workshop happens — running all seven steps in silence is a demo, not a workshop.

Adapt as you go. If the room is deep in the research, stay there. If they're impatient, skip to tokens.

---

## If something breaks

| Problem | What to do |
|---|---|
| Mobbin returns `[]` for everything | Write up what you can verify, draw wireframes for the rest, label them `wireframe — capture unavailable`. Say so out loud. Never describe a screen from memory. |
| Figma bridge unreachable | Re-run the checks in `AGENTS.md`. It fails silently more often than loudly. |
| A font won't load | Fall back to a serif you have installed |
| Agent reports success but Figma looks wrong | Ask it to re-read the node and report actual bounds. A claim of success isn't evidence. |

---

## Done when

- A chosen variation exists in Figma at phone width
- Its colours, spacing, radius and type all resolve from Figma variables and text styles
- `assets/DESIGN.md` is the stated source of those tokens
- The room has seen the variables appear live in Figma's sidebar
- You've named one thing the tokens improved **and** one thing they broke, with a measurement
- The chosen variation is ready for `session-2.md`
