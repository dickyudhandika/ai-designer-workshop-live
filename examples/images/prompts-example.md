# Image Prompts for Photo Marketplace Homepage

**Example output.** 4 placeholder slots from the Session 1 homepage, rendered as 6 prompt blocks — the featured collection is a *set*, so it gets written as three coordinated prompts.

Every block follows `session-2/image-prompt-template.md` exactly: all 8 sections, in template order, nothing renamed or dropped.

---

```
File:          Photo Marketplace Homepage (Figma)
Placeholders:  4 slots / 6 prompt blocks
Grid read:     hero (1200×600) · grid card (400×300) · featured collection (3 × 420×280) · category thumbnail (160×120)
Palette:       warm-white canvas #FDFCF8 · muted #F3F1EB · primary #1A5EFF (single CTA)
Generated:     2026-09-24
```

---

## Placeholder 1 — Hero Image (1200×600px)

Hero slot, 2:1. Wide editorial landscape sets the marketplace tone; the left third must stay uncluttered so the headline and search overlay sit cleanly.

```text
[PHOTOGRAPHY TYPE & SUBJECT] :
Editorial landscape photography. A vast mountain range viewed across a still glacial lake at golden hour, three ridgelines receding into haze, the nearest peak sharp and detailed, the furthest dissolving into pale blue-grey atmosphere.

[SUBJECT ACTION] (subject position)
The landscape is static and grounded — the lake occupies the lower third as a flat reflective plane, the ridgelines hold a strong horizontal in the upper two-thirds, and the frame is anchored by a single dark rock outcrop at the lower right. Everything sits on its own horizon; nothing floats.

[ENVIRONMENT] –
Glacial valley at high altitude. Foreground of smooth wet shoreline stones; midground of still, glass-like water; background of layered mountain ridges. Sky is a graded gradient from warm pale gold near the horizon to cool pale blue at the top. No vegetation taller than scrub. No structures, no people, no boats.

[LIGHTING] (direction, type, mood, shadows)
Low natural sunlight from the far right, roughly 15 degrees above the horizon — golden hour, warm (approx 3400K) with cool blue shadow fill on the left faces of the ridges. Mood is serene, expansive, and quietly dramatic. Shadows are long, soft-edged and directional, raking across the ridgelines; the lake carries a mirror reflection with slight ripple distortion.

[CAMERA] (angle, lens feel, depth of field, focus)
Wide angle, approximately 24mm, shot from a slightly elevated position near eye level with the shoreline. Deep depth of field — the foreground stones and the furthest ridge are both acceptably sharp. Horizon dead level and placed at the lower third. Overall reads as a considered medium-format landscape, not a snapshot.

[TEXTURE & PROPS] (materials, surface details, added elements)
Wet stone texture with visible grain and thin water sheen; fine ripples across the lake surface catching specular highlights; atmospheric haze between the ridgelines; faint cirrus streaking in the upper sky. No props, no added objects.

[STYLE KEYWORDS]
cinematic, golden hour, epic scale, warm tones, natural, editorial landscape, atmospheric depth

[CONSTRAINTS]
No text overlays. No logos. No watermarks. No people or animals. No buildings or man-made structures. Maintain natural colour grading — no heavy HDR, no oversaturated sky. Keep the left third low in visual complexity so a headline can overlay it. Do not add a sun flare.
```

---

## Placeholder 2 — Grid Card 3 (400×300px)

Grid inventory slot, 4:3. Commercial stock — a single subject that still reads clearly at 280px wide. This is the photo the marketplace is selling; it needs to look deliberate rather than candid.

```text
[PHOTOGRAPHY TYPE & SUBJECT] :
Commercial portrait photography. A woman in her early thirties, medium-dark skin, short natural curly hair, wearing a plain oatmeal linen shirt — head and shoulders in frame, looking directly into the lens with a calm, level, faintly warm expression.

[SUBJECT ACTION] (subject position)
Standing, weight slightly on the left foot, shoulders relaxed and squared to the camera, head level with a very slight tilt of no more than five degrees. Chin neither lifted nor dropped. Hands out of frame. She is anchored, not floating — the shoulders fill the lower frame edge so her body continues beyond the crop.

[ENVIRONMENT] –
Seamless studio backdrop in warm light grey with a subtle vertical falloff, darker at the edges and lighter directly behind the subject's head. Nothing else in frame — no props, no furniture, no architectural detail. The neutral background is chosen so the card's caption and price metadata read cleanly beneath the image.

[LIGHTING] (direction, type, mood, shadows)
Soft studio lighting — large softbox at approximately 45 degrees camera left and slightly above head height, with a white reflector filling from camera right at chin level. Mood is approachable and professional, not corporate-stern. Shadows are soft and open with no hard edge on the nose or jaw; a gentle gradient on the right cheek separates the head from the backdrop. Catchlights visible in both eyes at the upper left of the iris.

[CAMERA] (angle, lens feel, depth of field, focus)
Eye-level, approximately 85mm portrait focal length. Shallow depth of field — the eyes and the near cheek are critically sharp, the ears and the backdrop fall gently out of focus. Subject centred with a small amount of headroom. Vertical-centred framing that survives cropping to 4:3.

[TEXTURE & PROPS] (materials, surface details, added elements)
Visible skin texture and natural pores — retain fine detail, no heavy retouching or smoothing. Linen fabric weave legible on the collar and shoulders. Natural curl definition in the hair with individual flyaway strands. Subtle sheen on the lips and the bridge of the nose.

[STYLE KEYWORDS]
commercial portrait, natural skin texture, soft studio light, neutral backdrop, warm neutral, approachable, stock photography

[CONSTRAINTS]
No text, no logos, no brand marks. No shape distortion. No skin smoothing or beauty-filter effect. No background props or furniture. Keep the subject exactly as described — do not change hair length, skin tone, or expression. No watermark. No border or frame edge in the image itself. Leave the lower 10% of the frame visually quiet for the caption strip.
```

---

## Placeholder 3 — Featured Collection "Curated — Fog & Concrete" (3 × 420×280px)

A **set**, not a single image. Cohesion outranks any one frame, so all three prompts share one treatment — read the set line first, then the three prompts.

```
SET TREATMENT (applies to 3a, 3b and 3c — hold these constant):
  Light direction   soft diffuse side light from camera left, overcast
  Colour temperature  5200K, cool — palette of slate grey, moss green, fog white
  Camera treatment  35mm equivalent, deep focus, eye level, horizontal composition
  Mood   quiet, structural, mist-laden — the city disappearing into weather
```

### 3a — Fog at the concrete stairwell

```text
[PHOTOGRAPHY TYPE & SUBJECT] :
Architectural editorial photography. A brutalist concrete exterior stairwell, one flight visible at an oblique angle, with two thin moss-green weeds growing from the joint between the landing slab and the wall.

[SUBJECT ACTION] (subject position)
The structure is static and grounded, filling the frame from the bottom edge upward. The stair flight rises diagonally from lower left to upper right, the landing slab holds a firm horizontal, and the weeds sit upright in the wall joint. Nothing floats; every element rests on or against the concrete.

[ENVIRONMENT] –
Exterior concrete building in heavy fog. Visible surfaces: the stair treads and risers, the landing slab, a board-formed concrete wall on the right, and a thin metal handrail. The fog behind the structure dissolves every further layer into flat pale grey — no sky, no street, no other buildings readable. Surface is wet from recent rain.

[LIGHTING] (direction, type, mood, shadows)
Diffuse overcast daylight from camera left, completely soft with no directional source visible. Mood is quiet, cold and slightly melancholic. Shadows are almost absent — soft ambient occlusion only, in the tread joints and under the landing. The fog itself acts as a giant softbox, flattening contrast and muting the far edge of the structure.

[CAMERA] (angle, lens feel, depth of field, focus)
Slightly below the first tread, eye level with the landing, approximately 35mm. Deep depth of field — the near tread edge and the fog-veiled wall are both readable. Strong diagonal composition left by the stair flight; the frame is horizontal and the stair exits the top-right corner.

[TEXTURE & PROPS] (materials, surface details, added elements)
Board-form concrete texture with visible shutter lines and a few tie-rod holes. Rain-darkened patches and thin water films on the treads and the landing. Fine surface aggregate grain in the concrete. Moss-green weed leaves with soft matte texture. Slight oxidation on the handrail.

[STYLE KEYWORDS]
brutalist, fog, concrete texture, editorial architecture, slate and moss, cool overcast, quiet, structural

[CONSTRAINTS]
No text, no signage, no graffiti, no logos. No people. No shape distortion of the structure. Maintain the cool overcast grading — no warm tint, no sun. Keep the geometry exactly as described. No watermark.
```

### 3b — Fog-white corridor between slabs

```text
[PHOTOGRAPHY TYPE & SUBJECT] :
Architectural editorial photography. A narrow gap between two parallel raw concrete slabs — a slot of pale fog-white sky visible between them, running vertically through the frame, with a single moss-green seam at the base where the slabs meet the ground.

[SUBJECT ACTION] (subject position)
Both slabs stand vertical and grounded, rising beyond the top of the frame in a hard parallel. The fog-white gap between them is the visual subject and holds a clean vertical. The base is anchored by the wet ground plane at the lower edge. Nothing floats.

[ENVIRONMENT] –
Exterior concrete structure seen from directly inside the gap. Visible: the inner faces of both slabs, the wet ground between them, and the flat fog-white negative space beyond. No sky detail, no horizon, no surrounding context — the fog erases everything past the slab edges.

[LIGHTING] (direction, type, mood, shadows)
Diffuse overcast light entering from above between the slabs, soft and directionless, from camera left in bias. Mood is enclosing, cold and minimal. The inner slab faces sit in gentle ambient shadow deepening toward the base; the fog gap reads as the brightest value in the frame with no discernible shadow edge.

[CAMERA] (angle, lens feel, depth of field, focus)
Eye level, approximately 35mm, centred — a deliberately symmetrical one-point composition with the fog gap on the vertical centre. Deep focus, sharp from the near slab edge to the fog. Horizontal frame with strong vertical divisions at roughly the one-third and two-third lines.

[TEXTURE & PROPS] (materials, surface details, added elements)
Raw concrete faces with visible pour lines, tie-rod holes, and fine pitting. Wet ground with a thin water film and a faint reflection of the fog gap. Moss-green growth as a soft dark seam along the base joint. No props, no added objects.

[STYLE KEYWORDS]
brutalist, fog, negative space, editorial architecture, minimal, slate grey, cool overcast, symmetrical

[CONSTRAINTS]
No text, no signage, no graffiti, no logos. No people. No shape distortion. Maintain the cool overcast grading and the muted palette. Keep the composition symmetrical as described. No watermark.
```

### 3c — Rain-beaded handrail, moss green

```text
[PHOTOGRAPHY TYPE & SUBJECT] :
Architectural detail photography. A thin steel handrail seen edge-on, raking diagonally across the frame, with an even row of suspended rain beads along its lower edge and a soft moss-green concrete wall behind it.

[SUBJECT ACTION] (subject position)
The handrail is static and structurally supported — it enters the frame at mid-left, rises toward the upper right, and is anchored by a visible vertical post at the left third. Beads of water hang below its lower edge. Nothing floats; the rail has an evident support and gravity is respected.

[ENVIRONMENT] –
Exterior concrete wall with a steel handrail mounted on short standoffs. Visible: the rail, two standoffs, the post, and a shallow depth of bare concrete wall behind. The fog makes the wall surface dissolve into flat pale grey beyond roughly one metre. Wet concrete surface.

[LIGHTING] (direction, type, mood, shadows)
Soft diffuse overcast light from camera left, high and even. Mood is quiet, cold, tactile. Shadows are soft and minimal — a faint ambient gradient beneath the rail on the wall, no cast shadow edge. Each rain bead carries a small bright specular highlight on its upper-left shoulder.

[CAMERA] (angle, lens feel, depth of field, focus)
Eye level, approximately 35mm, close — the rail runs near-diagonally from lower left to upper right and is the sharpest element across the full frame. Deep focus; the wall behind is soft but not blurred into nothing. Horizontal composition with the rail crossing at roughly twenty degrees.

[TEXTURE & PROPS] (materials, surface details, added elements)
Steel rail with a smooth, faintly satin machined surface and light oxidation speckle near the standoff joints. Suspended rain beads, individually resolved, with clear specular highlights and slight refraction. Concrete wall with fine aggregate grain, wet sheen, and a soft moss-green tint in the lower band. No props beyond the rail hardware.

[STYLE KEYWORDS]
architectural detail, rain beads, steel and concrete, editorial, moss green, cool overcast, tactile, quiet

[CONSTRAINTS]
No text, no signage, no logos. No people. No shape distortion of the rail or hardware. Maintain the cool overcast grading and the shared slate/moss/fog-white palette. No watermark.
```

---

## Placeholder 4 — Category Thumbnail "Business" (160×120px)

Category bar slot, 4:3, rendered at 160×120. Must be unmistakable at thumbnail size — high subject-to-frame ratio, no busy background, no ambiguity with any other category in the row.

```text
[PHOTOGRAPHY TYPE & SUBJECT] :
Commercial business photography. A clean overhead desk scene — a closed dark grey laptop centred slightly right, a plain white ceramic mug with black coffee to its left, and an open blank notepad with a dark pen laid diagonally across it — read as a single unmistakable "business/office" subject even at 160px wide.

[SUBJECT ACTION] (subject position)
All objects lie flat and grounded on the desk surface, seen from directly above — laptop closed and squared, mug upright, notepad flat with the pen resting on top. Nothing stands, leans, or floats. The composition is a deliberate still life, not a candid snapshot.

[ENVIRONMENT] –
A light warm-grey desk surface filling the entire frame, no visible edge, no floor, no room. Nothing behind the objects — the surface is the whole environment, which keeps the subject-to-background ratio high enough to read at thumbnail size.

[LIGHTING] (direction, type, mood, shadows)
Soft even studio light from above and slightly camera left. Mood is calm, professional, daylight-neutral. Shadows are soft and short, falling down and to the right beneath the laptop and mug, with a gentle contact shadow that grounds each object on the surface. No harsh specular hotspots.

[CAMERA] (angle, lens feel, depth of field, focus)
Directly overhead, top-down, approximately 40mm equivalent. Deep depth of field — all three objects are equally sharp across the frame. Symmetrical overhead composition with the laptop group centred and a small clear margin on all four sides so nothing clips at the 4:3 thumbnail crop.

[TEXTURE & PROPS] (materials, surface details, added elements)
Matte laptop lid with a fine brushed finish, no visible branding. Glazed ceramic mug with a slight rim highlight. Off-white uncoated notepad paper with visible fibre. Dark pen with a smooth matte barrel. Light warm-grey desk surface with a very fine matte grain. No other props — no plants, no phones, no papers stacked at the edge.

[STYLE KEYWORDS]
business, overhead desk, minimal still life, neutral grey, professional, clean, stock photography, top-down

[CONSTRAINTS]
No text, no logos, no brand marks, no visible screen content. Blank notepad pages only. No people, no hands. No shape distortion. Keep the subject exactly as described — do not add or remove objects. Maintain generous margins so nothing clips when cropped to 160×120. No watermark.
```

---

## Notes for the live session

- **Placeholders 3a–3c are one deliverable.** If the three prompts drift in light direction or colour temperature, the collection band stops reading as curated and the whole featured section loses its point. Write the set treatment line first, then write into it.
- **The category thumbnail is the hardest of the four.** A 160px render forgives nothing — the reason this prompt strips the environment to a bare surface and bans every extra prop is legibility, not minimalism for its own sake.
- **Every prompt forbids text and logos.** These are stock images for a marketplace grid. An embedded wordmark is not a style choice; it makes the image unsellable.
- **`[CONSTRAINTS]` is not boilerplate.** The last line of each block is the one that stops the model inventing signage on the concrete, a brand mark on the laptop, or a sun flare on the hero.
