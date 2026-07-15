# Altera Labs Design System · v2 "The Reading Room".

This is the design-system reference for **Altera Labs v2, "The Reading Room"**: the warm, editorial brand identity for everything outward-facing. Altera is an AI Socratic tutor that builds a live mastery model of every student in a Canvas course, so instructors know what to re-teach before the next class. Under the hood that means a Cognitive Core knowledge graph, a Sustainable Mastery Index (SMI), and Bayesian Knowledge Tracing, built at JHU's Pava Center with partners JHU/Pava, NVIDIA Inception, Google Cloud, and Canvas.

"The Reading Room" treats the brand like an academic press: warm cream paper, deep-ink Fraunces serif headlines, royal-blue reserved strictly for data, terracotta and ochre for warmth, and a painted-paper **collage** signature in which the Cognitive Core is assembled from many paper "concept" tiles. It deliberately replaces the old cold "Deep Space Lab" dark identity, **for the marketing and brand layer only.** The product application is still on the v1 dark theme. That boundary is real and load-bearing; see the SEAM subsection below.

If you are about to build a marketing surface, a brand asset, a deck, or a landing page, this document is the contract. The literal source of truth for values is `colors_and_type.css`. Never invent a hex; reference a token var name.

---

## Sources.

The system spans two repositories. Know which one you are in before you touch a color.

| Repo | Layer | Theme | Visibility | What lives here |
| --- | --- | --- | --- | --- |
| `altera-laboratories/Altera-Labs` | Product application | **Dark, "Deep Space Lab" (v1)** | Private | The actual tutor app: chat, Cognitive Core graph view, SMI dashboards, Canvas integration. Still v1 dark. Do **not** apply Reading Room paper tokens here without a migration plan. |
| `altera-laboratories/altera_webpage` | Marketing site and brand | **Light, "The Reading Room" (v2)** | Public-ish (marketing) | Landing pages, brand assets, this design system, `colors_and_type.css`, collage art direction. This is where v2 lives. |

When a task says "the site," "the brand," "the marketing page," or "the deck," it means `altera_webpage` and this v2 system. When it says "the app," "the product," "the graph view," or "the dashboard," it means `Altera-Labs` and v1 dark. If you are unsure, ask before you ship a color across the seam.

---

## Index of files.

| File | Role |
| --- | --- |
| `README.md` | This document. The design-system overview and rulebook. |
| `SKILL.md` | The Agent-Skill invocation contract: when to use this system and how. |
| `colors_and_type.css` | **The token contract.** All color, type, radii, shadow, and motion variables. The single source of truth for values. |
| `preview/` | Rendered foundation and component reference cards: surfaces, accents, mastery, type scale, mono data labels, eyebrows, buttons, pills, paper cards, the collage signature, radii, shadows. |
| `ui_kits/marketing/index.html` | The marketing hero reference, built to the v2 system and wired to the tokens. |

When you add a new token, edit `colors_and_type.css` first, then update the relevant table in this README so the two never drift.

---

## Content fundamentals.

### Voice.

Numbers-with-sources, quietly confident, never breathless. We are an academic press describing a research instrument, not a startup shouting. Real Altera copy only. No lorem, no placeholder claims, no invented statistics.

| Trait | Do | Don't |
| --- | --- | --- |
| Precise | "Altera builds a live mastery model of every student in a Canvas course." | "Altera revolutionizes learning with AI." |
| Sourced | Every number carries a source or a clear basis (SMI, BKT, a named study). | Round numbers with no provenance. |
| Calm | "Instructors see what to re-teach before the next class." | "10x your classroom outcomes!!" |
| Concrete | Name the mechanism: Cognitive Core, SMI, Bayesian Knowledge Tracing. | Vague "machine learning magic." |
| Restrained | Let the typography and paper carry the tone. | Exclamation stacks, hype adjectives, hedge words. |

### Casing.

- **Section headings (H2) end with a period.** This is an Altera tic and it is required. "How it works." not "How it works".
- **Sentence case everywhere.** Headlines, buttons, nav, eyebrows. Capitalize the first word and proper nouns (Altera, Canvas, Cognitive Core, JHU, Pava, NVIDIA, Google Cloud) only.
- Eyebrows render uppercase via the `.eyebrow` class (mono, terracotta), so author them in sentence case and let CSS uppercase them.

### Status vocabulary.

Use the mastery semantics consistently and never recolor them for decoration:

| Status | Meaning | Token family |
| --- | --- | --- |
| High mastery | Concept is durable; no re-teach needed | `--mastery-high-fill` / `--mastery-high-stroke` (emerald) |
| Mid mastery | Partial; watch and reinforce | `--mastery-med-fill` / `--mastery-med-stroke` (amber) |
| Low mastery | Re-teach before next class | `--mastery-low-fill` / `--mastery-low-stroke` (rose) |
| Data / focus | A datapoint, an active focus, a chart axis | `--signal-500` (royal blue) |

Emerald = high, amber = mid, rose = low. This is product semantics, not a palette. Royal blue means "this is data or focus," nothing else.

### Numbers and sources.

State the number, then its basis, in the same breath. SMI figures, BKT confidence, cohort sizes, and partner facts (JHU/Pava, NVIDIA Inception, Google Cloud, Canvas) must be traceable. If a claim cannot be sourced, cut it.

### The NO-EMOJI rule.

**No emoji. Ever.** Not in copy, not in headings, not in UI, not in commit-adjacent brand assets. Where an icon is needed, use an inline SVG or a Lucide glyph (see Iconography). This is non-negotiable.

### The NO-EM-DASH rule (this reverses the old system).

**No em-dash characters (U+2014) anywhere.** Use commas, colons, periods, or a middot (·) for separation and aside. This **explicitly reverses** the previous design system, which told writers to "use em-dashes liberally." That guidance is dead. If you are porting old copy, the em-dashes go. A middot (·) is the approved choice for a tight inline separator, for example a metadata line like `SMI · live · per cohort`.

---

## Visual foundations.

### The Reading Room, in one breath.

Warm cream paper base. Deep-ink Fraunces display serif for headlines. Royal-blue used sparingly and only for data and focus. Terracotta and ochre for warmth, links, and marks. A painted-paper collage signature for the hero and for the Cognitive Core motif. Subtle paper grain over fills. It should feel like a well-set monograph from a university press, not a SaaS dashboard and emphatically not zinc-950.

### Color.

Use these exact token names. Do not hardcode the hexes; they are listed only so the table is legible.

**Surfaces (paper).**

| Token | Hex | Use |
| --- | --- | --- |
| `--paper-50` | `#faf5ea` | Lightest lift; insets, hovers |
| `--paper-100` | `#f3ead8` | **Page base.** The default cream canvas |
| `--paper-200` | `#ebdec5` | Cards |
| `--paper-300` | `#ddccac` | Dividers |
| `--paper-400` | `#c9b793` | Borders |

**Ink (text).**

| Token | Hex | Use |
| --- | --- | --- |
| `--ink-900` | `#1f1a14` | Headlines |
| `--ink-700` | `#3d3528` | Strong text |
| `--ink-600` | `#5a4f3e` | Body |
| `--ink-500` | `#7a6c56` | Muted |
| `--ink-400` | `#9c8c72` | Metadata |

**Accents.**

| Token | Hex | Use |
| --- | --- | --- |
| `--signal-500` | `#476ee3` | Royal blue. **Data and focus only.** Charts, active states, the live datapoint |
| `--signal-700` | `#2f4fb0` | Blue text on paper (darker, for contrast) |
| `--terracotta-600` | `#9c4a2f` | Links, eyebrows, editorial marks |
| `--terracotta-500` | `#c0603a` | Lighter terracotta accent |
| `--ochre-500` | `#cf8a3b` | Ochre warmth |
| `--ochre-600` | `#b5722a` | Deeper ochre |

**Mastery (product semantics, used in brand only to illustrate the model).**

| Token | Hex | Meaning |
| --- | --- | --- |
| `--mastery-high-fill` / `--mastery-high-stroke` | `#0f7a52` / `#1f9d6b` | High (emerald) |
| `--mastery-med-fill` / `--mastery-med-stroke` | `#c0791f` / `#e0a232` | Mid (amber) |
| `--mastery-low-fill` / `--mastery-low-stroke` | `#b5341f` / `#d6492f` | Low (rose) |

**Collage swatches** (the painted-paper tile palette; see Collage section).

| Token | Hex |
| --- | --- |
| `--swatch-parchment` | `#e7d9bd` |
| `--swatch-kraft` | `#b5722a` |
| `--swatch-ochre` | `#cf8a3b` |
| `--swatch-terracotta` | `#c0603a` |
| `--swatch-denim` | `#3f6b87` |
| `--swatch-sage` | `#6f8f5f` |
| `--swatch-slate` | `#5d6b7e` |
| `--swatch-ink` | `#2a241b` |
| `--swatch-signal` | `#476ee3` |

### Type.

| Role | Token | Family | Notes |
| --- | --- | --- | --- |
| Display (H1/H2/H3) | `--font-display` | Fraunces (serif) | Headlines. Heading tracking `--tracking-display` `-0.01em` |
| Body / UI | `--font-sans` | Inter | Body copy, buttons, nav |
| Data labels / eyebrows | `--font-mono` | JetBrains Mono | Data labels, eyebrows, mono metadata |

- Display scale top end: `--fs-display-xl` is `clamp(2.75rem, 6vw, 5.5rem)`.
- **Italic Fraunces emphasis** uses the `.display-accent` class, which renders in terracotta. Use it for the one word in a headline that carries the idea.
- Semantic classes already defined in `colors_and_type.css`: `.h1` `.h2` `.h3` `.h4`, `.display-accent`, `.body` `.body-lg`, `.metadata`, `.eyebrow` (mono terracotta uppercase), `.data-label` (mono), `.mono`. Use these rather than re-styling.

### Spacing.

Generous, like a printed page with real margins. Let copy breathe; the editorial feel comes from whitespace as much as from the serif. Prefer fewer, larger blocks over dense grids. Align to the page measure; long body text should sit at a comfortable reading width, not full-bleed.

### Backgrounds.

Backgrounds are **warm paper plus subtle grain, never zinc-950.** The base canvas is `--paper-100`. Layer `var(--paper-grain)` (an SVG turbulence data-URI) at low opacity with `mix-blend-mode: soft-light` over fills to get the paper tooth. The grain is a finish, not a texture you should notice consciously; if you can read it as noise, dial the opacity down.

### Cards.

Two card idioms:

- **Paper cards.** Surface `--paper-200`, dividers `--paper-300`, borders `--paper-400`. Radius `--radius-card`. Shadow `--shadow-paper` or `--shadow-paper-sm`. The default container.
- **Pinned notecards.** A card that reads as physically pinned to the page, using `--shadow-pin`. Use sparingly for a single highlighted artifact (a quote, a concept tile, a stat), not for every card.

### Radii.

| Token | Value | Use |
| --- | --- | --- |
| `--radius-pill` | `9999px` | Pills, tags |
| `--radius-button` | `8px` | Buttons |
| `--radius-md` | `6px` | Small elements |
| `--radius-card` | `10px` | Cards |
| `--radius-lg` | `16px` | Large panels, hero containers |

### Shadows.

| Token | Use |
| --- | --- |
| `--shadow-paper-sm` | Subtle lift on small paper cards |
| `--shadow-paper` | Standard paper card |
| `--shadow-pin` | The pinned-notecard look |
| `--shadow-signal` | Focus ring (royal-blue), for keyboard focus and active data states |

### Motion.

- Default easing is `--ease-soft` (`cubic-bezier(0.23, 1, 0.32, 1)`). Movement should feel like paper settling, soft and decelerating, never springy or bouncy.
- **Honor `prefers-reduced-motion`.** Wrap non-essential transitions and any hero animation in an `@media (prefers-reduced-motion: reduce)` guard that disables or near-instantly resolves them. The page must be fully usable and legible with motion off.

### Imagery.

Imagery is **painted-paper collage** (see the next section). Photography, when used, is warm and editorial and sits on paper, not on a dark stage. No stocky gradient-mesh "AI" art, no neon, no dark-space renders. Those belong to the retired v1 identity.

### Light marketing / dark product app SEAM.

This is the most important boundary in the system, so it gets its own subsection.

- **Marketing and brand (`altera_webpage`) are light, "The Reading Room," v2.** Paper tokens, Fraunces, collage. That is this document.
- **The product app (`Altera-Labs`) is still dark, "Deep Space Lab," v1.** It has not been migrated. Its mastery semantics (emerald/amber/rose) and royal-blue-for-data still hold, but its surfaces are dark, not paper.
- When a user crosses from the marketing site into the app, they cross this seam intentionally. Do **not** "fix" the app to match the brand on a whim; a theme migration of the product is a separate, scoped project. Do **not** leak dark `zinc-950` surfaces into the marketing site.
- The two themes share the **mastery color semantics** and the **meaning of royal blue** (data/focus). That shared vocabulary is what makes the seam coherent rather than jarring. Preserve it on both sides.

---

## Iconography.

- **Lucide only.** No emoji, ever (restating the hard rule because it is most often broken in iconography).
- Inline SVG is acceptable for bespoke marks (logo, the collage tile glyph). For UI affordances (arrows, check, external-link, menu), reach for Lucide.
- Tint icons with ink or accent tokens, not arbitrary colors. A data-related icon may take `--signal-500`; an editorial mark may take `--terracotta-600`; a default UI icon takes an ink token. Keep stroke weight consistent with Lucide defaults so glyphs read as a set.

---

## Collage and art direction.

The brand signature is the **Cognitive Core rendered as a paper collage.** The knowledge graph that the product computes is depicted, in the brand, as many painted-paper "concept" tiles assembled into a structure: each tile is a concept, the arrangement is the Core, and the seams between tiles are visible and deliberate. This is the visual thesis of v2, that learning is composed, tile by tile, into mastery.

### The paper-swatch system.

Tiles are drawn from the collage swatch tokens: `--swatch-parchment`, `--swatch-kraft`, `--swatch-ochre`, `--swatch-terracotta`, `--swatch-denim`, `--swatch-sage`, `--swatch-slate`, `--swatch-ink`, and `--swatch-signal`. Treat them as a set of "papers" you tear and place. `--swatch-signal` (royal blue) is the rare highlighted tile: the active concept, the live datapoint. Mastery-colored tiles (emerald/amber/rose) may appear when the collage is literally illustrating the mastery model; otherwise stay in the warm swatch range so blue keeps its data meaning.

### Where collage is allowed.

- **Hero art.** The primary place. The Cognitive-Core-as-collage is the hero motif.
- **Section dividers and feature illustrations**, in restrained doses, when they reinforce the "composed from concepts" idea.
- **Pinned notecards** can read as a single torn-paper tile.

Where collage is **not** allowed: dense UI, data tables, legal pages, anywhere it competes with copy for the reader's attention. The system is editorial first; collage punctuates, it does not wallpaper.

### Real art must be commissioned. The CSS version is a placeholder.

The CSS-rendered collage (layered divs, swatch fills, grain, soft shadows) is a **placeholder and a fallback, not the finished hero.** The real hero collage should be **commissioned or generated as painted-paper artwork** with genuine torn edges, fiber, and paint texture, then placed as an optimized image asset. Do not ship the CSS approximation as the final brand hero on a flagship page; use it to hold layout and as a graceful fallback (and as the reduced-motion or low-bandwidth state). When the commissioned art lands, it replaces the CSS placeholder, it does not sit alongside it.

---

## How to use.

1. **Identify the layer.** Marketing/brand (`altera_webpage`, v2 paper) or product app (`Altera-Labs`, v1 dark). Apply the right system. Respect the seam.
2. **Pull values from tokens, not memory.** Reference `colors_and_type.css` var names. If a value you need does not exist, add a token there first, then document it here.
3. **Use the semantic classes** (`.h1`...`.h4`, `.body`, `.eyebrow`, `.data-label`, `.display-accent`, `.metadata`, `.mono`) rather than restyling type from scratch.
4. **Write to the voice.** Numbers with sources, sentence case, H2s end with a period, no emoji, no em-dashes (middot · when you need a separator).
5. **Keep the semantics intact.** Emerald/amber/rose = high/mid/low mastery; royal blue = data/focus. Never recolor them decoratively.
6. **Ship paper, not zinc.** Backgrounds are `--paper-100` plus `var(--paper-grain)`. If you reach for a near-black surface on the marketing site, stop.
7. **Honor `prefers-reduced-motion`** and ease with `--ease-soft`.

---

## Caveats.

- **The token file wins.** If this README and `colors_and_type.css` disagree on a value, the CSS is correct and this README is stale; fix the README.
- **The product app is not migrated.** Anything you read here about paper and Fraunces does not yet apply inside `Altera-Labs`. Do not assume parity.
- **The hero collage is a placeholder in CSS.** Treat any CSS-built collage as provisional until commissioned art replaces it.
- **No-emoji and no-em-dash are hard client rules**, not style preferences. They override older guidance, including the previous system's pro-em-dash stance. Lint for them.
- **Do not invent hexes.** Every color must trace to a token var name. A raw hex in a marketing surface is a bug.
- **Restraint is the brand.** When in doubt, remove the flourish. The Reading Room earns its warmth from typography, paper, and whitespace, not from decoration.
