# Photo Marketplace Competitor Analysis

**Example output.** This is what a completed Phase 1 report looks like — specific observations, named competitors, cross-app patterns, one clear recommendation. Your agent's live report will differ in wording but should match this structure and this level of specificity.

Format reference: `session-1/report-template.md`

---

## Competitors Found

### 1. Unsplash — free, community-driven, photographer-first
- URL: https://unsplash.com
- Layout: Full-bleed edge-to-edge photo grid directly under a slim nav. No hero band, no marketing chrome. Photos start ~80px from the top of the viewport.
- Navigation: Single-row nav — logo left, five text links, "Submit an image" + "Log in" right. No mega-menu, no dropdowns.
- Color usage: Effectively monochrome. White canvas, near-black text, one subtle gray for secondary. Colour comes entirely from the photographs — the UI never competes.
- Typography: One sans family. Large regular-weight wordmark. Grid card titles are small and quiet — photographer name in a lighter gray than the title.
- Primary action: "Submit an image" in the nav. Contributor model — the primary ask is contribution, not purchase.
- Grid type: Masonry, mixed aspect ratios, variable column height. Density is high — 4–5 columns at desktop width.
- Search prominence: High. Search is a full-width input centered in the nav, the single widest element on the page.
- Filters: Appear as a horizontal row of category chips beneath the nav ("Editorial", "Wallpapers", "Nature", …). Sort control sits right-aligned above the grid.
- What works: Photos-forward to the point of erasing the interface — the product *is* the grid. Category chips give browsing without a click into a filter panel.
- What's weak: No editorial framing anywhere. A first-time visitor gets no explanation of what Unsplash is or how licensing works — that content lives three clicks away.

### 2. Shutterstock — paid, professional, enterprise-leaning
- URL: https://www.shutterstock.com
- Layout: Dense vertical stack — nav, search hero band, category row, then a mixed grid of collections and individual assets. Several distinct content bands before the first photo grid.
- Navigation: Two-tier. Utility row (language, pricing, "Sell your content") above a main row of category links with dropdown carets.
- Color usage: Red primary against white — the brand accent is used generously on CTAs, badges, and pricing tags. Busier than the free competitors.
- Typography: One sans family throughout, heavier weights. Card titles are denser and carry more metadata (asset type, contributor tier).
- Primary action: "Get 10 free images" / pricing CTA in the hero band. Buyer model — the ask is a plan, not a contribution.
- Grid type: Uniform-ish grid with occasional featured tiles spanning two columns. More regular than Unsplash, less rigid than a fixed card grid.
- Search prominence: Very high. Search is the hero band — a large input with a secondary filter dropdown ("Images", "Videos", "Music") attached to it.
- Filters: Persistent filter panel on the left of the results view; on the homepage, category tiles function as the filter entry point.
- What works: Metadata density — every card shows enough for a buyer to qualify the asset without opening it. Search-first framing matches buyer intent.
- What's weak: Cluttered by comparison. The photo grid doesn't start until well down the page, so the actual product is buried under merchandising bands.

### 3. Pexels — free, discovery-led, editorial-ish presentation
- URL: https://www.pexels.com
- Layout: Nav, then a large search-led hero band, then a category chip row, then a full-width masonry grid. Close to Unsplash but with a heavier hero.
- Navigation: Single-row nav — logo, four text links, "Upload" + "Join" right. Simpler than Shutterstock, slightly heavier than Unsplash.
- Color usage: White canvas with a teal/green accent used sparingly on links and the primary CTA. Mostly restrained — photos carry the colour.
- Typography: One sans family. Wordmark is bold; card titles are small and low-contrast. Similar hierarchy to Unsplash.
- Primary action: "Upload" (contributor) alongside "Join" (account). Both present, neither dominant — no single loud CTA.
- Grid type: Masonry with mixed ratios. Slightly lower density than Unsplash — larger cards, more space between columns.
- Search prominence: High. Search input sits in the hero band area, wider than in the nav-only pattern.
- Filters: Category chips under the hero plus a set of curated "Popular searches" links. Sort control above the grid.
- What works: Category chips are large and photographic themselves — browsing feels visual rather than taxonomic. Popular-search links shorten the path to a usable query.
- What's weak: Hero band eats vertical space without saying anything the grid doesn't already say. The dual CTA splits attention.

### 4. Getty Images — paid, editorial/agency, premium positioning
- URL: https://www.gettyimages.com
- Layout: Heavy nav, large hero band with a rotating editorial feature, then curated collection rows, then a grid. The most content bands before the first raw grid of all five.
- Navigation: Two-tier with a prominent utility row. Multiple dropdown menus, long category taxonomy.
- Color usage: Black-and-white-dominant with a bright accent on CTAs. Deliberately restrained — reads as premium rather than commercial.
- Typography: One sans family, editorial weight and spacing. Larger headline type than any other competitor surveyed.
- Primary action: Search, plus a subscription/pricing CTA. Editorial-first — the hero promotes a curated story, not a plan.
- Grid type: Mixed — editorial collection rows (uniform hero tiles) followed by a more irregular results grid further down.
- Search prominence: Highest of the five by measure — a very wide search input at the top of the hero with an inline media-type selector.
- Filters: Deep. Date, licence type, orientation, collection, and colour filters. Overkill on the homepage, appropriate in results.
- What works: Editorial curation is a genuine differentiator — the homepage tells a story rather than dumping a catalogue. Premium restraint in colour reads as authority.
- What's weak: The most cluttered above-the-fold of all five. Filter depth is intimidating for a casual visitor and mostly dead weight on the homepage.

### 5. Adobe Stock — paid, bundled, Creative-Cloud-integrated
- URL: https://stock.adobe.com
- Layout: Nav, hero search band, category tiles, then a grid that mixes collections and assets. Structured and banded, close to Shutterstock in rhythm.
- Navigation: Single-row nav with a dropdown for asset type and prominent links to Creative Cloud products.
- Color usage: White canvas with Adobe's brand red on primary actions only. Otherwise neutral — the most restrained paid competitor.
- Typography: Adobe's own sans family. Consistent with the parent product suite — same type voice across the ecosystem.
- Primary action: "Start free trial" / pricing. Buyer model, but the CTA is framed as a trial rather than a plan.
- Grid type: Uniform grid with occasional spanning feature tiles. The most regular grid of the five.
- Search prominence: High. Large search band with a media-type dropdown attached, mirroring the Shutterstock pattern.
- Filters: Asset-type switch at the top, then a left-hand filter panel in results. Homepage uses category tiles as the entry point.
- What works: Uniform grid makes pricing and licensing comparison easy — a buyer can scan and decide. Integration messaging ("included with Creative Cloud") is a strong differentiator.
- What's weak: Uniform grid is the least exciting presentation of photographs — the images feel like catalogue entries rather than work. Least visually distinctive of the five.

---

## Cross-App Patterns

**Industry standards (3+ of 5 agree — match these or look amateur):**

- **Prominent search in the nav.** All 5. Every competitor makes search the widest, highest-contrast element above the fold. On a photo marketplace, searching *is* the primary task.
- **Flexible grid over uniform grid.** 4 of 5 (Unsplash, Shutterstock, Pexels, Getty) use masonry or partially spanning grids. Only Adobe Stock runs a fully uniform grid. Photographs have different aspect ratios; cropping them all into one shape loses the work.
- **Minimal colour palette.** 3 of 5 (Unsplash, Pexels, Getty) stay near-monochrome and let the photographs supply the colour. The two that use a strong brand accent (Shutterstock, Adobe Stock) do it because they're selling plans — the accent carries conversion weight.
- **Category chips or tiles as the browse entry point.** All 5. Nobody expects a first-time visitor to type a query; a horizontal chip row or tile set gives a zero-thought browse path.
- **Search first, filters second.** All 5 push deep filtering into the results view. Nobody burdens the homepage with a full filter panel.

**Differentiators (1–2 of 5 — safe to adopt, hard to copy):**

- **Editorial curation as content.** Getty is the only one telling a story on the homepage. Everyone else shows a catalogue. For a free or community-positioned marketplace this is cheap to do and unusually distinctive.
- **Photographic category chips.** Pexels renders its chips with images, not just labels — browsing feels visual. Nobody else does this.
- **Metadata density as a buyer tool.** Shutterstock puts asset type and tier on the card. For a paid product this reduces the click-to-qualify cost; for a free product it's noise.

**Positioning split (this drives every other decision):**

- **Free / community model — Unsplash, Pexels:** primary CTA is *contribution* ("Submit an image", "Upload"). The homepage is a gallery. Colour is minimal because nothing needs to convert. Trust is built by showing volume and quality of work.
- **Paid / professional model — Shutterstock, Getty, Adobe Stock:** primary CTA is *purchase* (plan, trial, pricing). The homepage is a merchandising surface. There's a pricing or subscription band, deeper taxonomy, and either a strong accent colour or a deliberate premium restraint doing the conversion work.

**Common frustration point (opportunity):**

None of the five handle the *empty or thin result* state well, and none of them explain licensing clearly at the point of browsing — a licence badge is rare on a grid card. For a new marketplace, "what can I actually do with this photo" is an unclaimed position on the homepage.

---

## Recommendation

**Pick:** Unsplash

**Why:** Unsplash is the only competitor whose above-the-fold is *only* the product — a slim nav, a full-width search, and a dense masonry grid that starts immediately. It maps cleanly onto the DESIGN.md baseline: warm-white canvas (`#FDFCF8`), near-monochrome palette, one restrained accent for the single primary action, sharp 0px edges, and Fauna One titles against Inter for everything else. The minimal-chrome approach also means the photographs are the only source of colour, which is exactly what the token system is built for — `primary` reserved for the one CTA, `border` for separation only.

Two things to take and one to leave:

- **Take** Unsplash's immediate-grid density and its chip row — the browse path is the differentiator.
- **Take** Getty's editorial framing, in a light dose — one curated collection band below the grid, not a full hero story. It's the cheapest way to look unlike the catalogue competitors.
- **Leave** Unsplash's CTA ambiguity. Unsplash's "Submit an image" is quiet to the point of being invisible. The homepage needs one unmistakable primary action, and it should be search — with a single `primary`-coloured CTA beside it.
