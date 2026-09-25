# Image-Grid Marketplace Competitor Analysis (Mobile)

Example output — the content standard. This is what a completed Phase 1 report reads like.

> **Why these five?** Session 1 builds a **photo marketplace app**. The references are **image-grid
> marketplace apps**, because that is where the mobile evidence actually lives: one of ten named
> stock-photo brands has usable app screens on Mobbin, while image-grid marketplaces are everywhere.
> Same design problem — a mobile homepage showing a searchable grid of photographs — far better
> evidence. Every field below is filled from a real screen.

**Source:** Mobbin `search_screens`, `platform: ios`
**Probe query:** `"marketplace app home screen with photo grid and search bar"`
**Capture:** app screens at Mobbin native 1179×2676 (1:2.270)
**Date:** 2026-09-24

---

## Competitors Found

### 1. Depop — second-hand fashion, community-led
- URL: https://www.depop.com
- Capture: app screen
- Layout: Top bar: full-width search field + camera, heart, bag icons. A greeting, "Hey Sam!", then a 2-column product grid. No hero, no campaign band — the grid is the page.
- Nav & search: Search is a full-width field in the top bar, always visible, never collapsed to an icon. Bottom tab bar: Home, Discover, Sell (raised, centre), Inbox, My Depop.
- Grid: 2 columns, uniform cards, tight gutters. Price, brand and size sit on every tile.
- Primary action: "Sell" — the raised centre button in the bottom tab bar.
- Mobile pattern: Greeting-led home feed: "Hey Sam!" personalises the top of the page and the grid follows immediately. Bottom tab bar with a raised centre Sell button — the only commerce action in the thumb zone.
- Works: Grid-first — no promo band, no hero. Photographs start within the first 120px and stay the subject of the page.
- Weak: The search field carries no scope control — one field for sellers, brands and items alike.

### 2. Vinted — second-hand fashion, mass-market
- URL: https://www.vinted.com
- Capture: app screen
- Layout: Search field, then category tabs (All / Designer / Electronics), then a personalisation banner, then "Recommended for you" above a 2-column grid.
- Nav & search: Search field pinned at the top, category tabs directly beneath it. Bottom tab bar: Home, Search, Sell, Inbox, Profile — Home active.
- Grid: 2 columns, mixed item ratios, price with "incl." and condition labels on each tile.
- Primary action: "Personalize" inside the banner — set sizes and brands to filter the feed.
- Mobile pattern: Category tabs directly under the search field: scope is visible and switchable without opening anything. Bottom tab bar with Search promoted to a first-class tab beside Home.
- Works: Search and category tabs share the top block, so scoping the catalogue costs no extra tap target.
- Weak: A full-width promo banner sits above the first product — the marketplace is sold to before it is shown.

### 3. Vestiaire Collective — luxury resale, editorial
- URL: https://www.vestiairecollective.com
- Capture: app screen
- Layout: "Now Trending" with a horizontal card carousel, then "Dreaming of Dresses" as a second band. Editorial sections rather than one flat grid.
- Nav & search: Top bar: bell, full-width search field ("Search for items, members…"), bag. Bottom tab bar: Home, Shop, Sell, Favourites, Me.
- Grid: Horizontal carousels of large cards, not a fixed column grid. Prices sit on the card's lower edge.
- Primary action: "View all" under each band — the escape hatch from a curated rail to the full list.
- Mobile pattern: Horizontal carousel bands instead of a vertical grid: several curated rails stacked, each with its own "View all". Search is still pinned full-width in the top bar.
- Works: Luxury reads as editorial — fewer, larger photographs per screen and generous whitespace. The images carry the value.
- Weak: No dense grid anywhere on the home screen — only two or three items are visible per band, so browsing is slow.

### 4. Etsy — handmade and vintage marketplace
- URL: https://www.etsy.com
- Capture: app screen
- Layout: Search field with a concrete example placeholder, then a promo banner, then "Shop by category" tiles, then "Home Decor" as a curated row.
- Nav & search: Search is the first element on the page and its placeholder carries a live example query. Bottom tab bar: Home, Search, Favorites, You, Cart — Home active.
- Grid: Mixed: 2x2 product tiles inside named sections plus a small category-tile row. Not one continuous grid.
- Primary action: "Explore more" beside each section heading, and "Get this gift" on the banner.
- Mobile pattern: Search field first with an example placeholder, then category navigation, then curated product rows. Every section is labelled and carries its own "Explore more".
- Works: The search placeholder shows a real example query — it teaches what the catalogue contains before you type.
- Weak: Category tiles and editorial sections push the actual product grid below the first screen.

### 5. Nextdoor — local listings, filter-driven
- URL: https://nextdoor.com
- Capture: app screen
- Layout: Search field, then filter chips (All categories, Free, 15 mi, Most Relevant), then a 2-column listings grid.
- Nav & search: Search field at the top; scope controls appear as chips directly beneath it, each showing its current value. Bottom tab bar: Home, Search, For Sale, Faves.
- Grid: 2 columns of listings with price, distance and age on each tile. Ad tiles sit inline with real inventory.
- Primary action: The filter chips — distance and category are what make the feed usable.
- Mobile pattern: Chips-above-grid as the scope control: category, price and distance each visible and tappable in place, with no sheet or drawer. The only one of the five to run inline ad tiles.
- Works: Filter chips sit above the grid and show their own state, so the scope is legible without opening a panel.
- Weak: Sponsored tiles are visually indistinguishable from real listings until you read the label.

---

## Cross-App Patterns

**Industry standards**

- Search is the first element on every home screen — a full-width field in the top bar, not an icon. 5 of 5.
- A 2-column grid is the default catalogue view. 3 of 5 (Depop, Vinted, Nextdoor); the other two use editorial carousels or labelled rows.
- Bottom tab bars everywhere, and search is promoted to a first-class tab in 4 of 5.

**Differentiators**

- Scope controls sit above the grid as visible chips or tabs — category, distance, condition. 3 of 5.
- Only Depop puts a commerce action (Sell) in the bottom bar's thumb zone. The other four leave the bottom third to passive tabs.

**Opportunity**

- Opportunity: no competitor puts a persistent search or filter control in the bottom third. The nearest field to a thumb is still in the top 10% of the viewport — an unclaimed, mobile-native position.

---

## Recommendation

**Pick:** Depop

**Why:** Depop is the only one of the five whose home screen is a pure grid — no promo band, no hero,
photographs starting within the first 120px. It carries price, brand and size on every tile, pins a
full-width search field in the top bar, and is the only app to put a real commerce action in the
bottom tab bar. Its two weaknesses — a scope-less search field and no filter chips — are both
fixable, which gives Phase 3 a brief rather than a template to copy.

**Chosen:** Depop (human pick — awaiting confirmation in session)
