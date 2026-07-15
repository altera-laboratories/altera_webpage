---
name: altera-reading-room
description: >
  Altera Labs v2 "The Reading Room" brand kit. A warm-light editorial identity
  (warm cream paper, deep-ink Fraunces serif, royal-blue reserved for data,
  terracotta/ochre warmth, painted-paper collage signature) for Altera's
  marketing and brand surfaces. Invoke when building or restyling any public
  Altera brand surface: landing pages and marketing sections, pitch and partner
  decks, social and OG images, eyebrow/data-label callouts, or any new
  outward-facing section that must read like an academic press. Altera is an AI
  Socratic tutor that builds a live mastery model of every student in a Canvas
  course (Cognitive Core knowledge graph, Sustainable Mastery Index / SMI,
  Bayesian Knowledge Tracing; built at JHU's Pava Center; partners JHU/Pava,
  NVIDIA Inception, Google Cloud, Canvas). Do NOT invoke for the product/app
  itself: those surfaces still run the v1 dark "Deep Space Lab" system.
---

# Altera v2: The Reading Room

The marketing and brand identity for Altera Labs. It is a warm, light, editorial
system, built to feel like an academic press: warm cream paper, deep-ink Fraunces
serif headlines, royal-blue reserved for data and focus, terracotta and ochre for
warmth, and a painted-paper collage signature where the Cognitive Core is
assembled from many paper "concept" tiles.

This deliberately replaces the old cold "Deep Space Lab" dark identity for the
marketing and brand layer only.

## The seam (read this first).

There are two living identities. Know which one you are touching before you write
a single rule.

- **v2 "The Reading Room"** (this kit): light, warm, editorial. Marketing site,
  brand pages, decks, social/OG, partner-facing surfaces. Cream base, ink serif,
  collage.
- **v1 "Deep Space Lab"**: the dark product app. The logged-in experience, the
  graph workspace, the in-app UI. It is NOT in scope here and does NOT adopt
  these tokens.

If the surface is something a logged-in student or instructor uses, it is v1.
If it is something a prospect, partner, or reader sees before they sign in, it
is v2. When in doubt, ask.

## When to use.

Use this kit for Altera's outward-facing brand and marketing surfaces:

- Marketing site pages and new marketing sections (hero, how-it-works, the
  Cognitive Core explainer, SMI/mastery story, partners, pricing, about, footer).
- Pitch decks, partner decks, and investor or grant one-pagers built in HTML/CSS.
- Social cards and Open Graph / share images.
- Eyebrows, data labels, pull quotes, notecards, and any editorial callout that
  carries Altera's "numbers with sources" voice.
- Brand refreshes of existing marketing copy and layout into the warm editorial
  language.

If the surface is public, pre-login, and meant to persuade or explain, it
belongs here.

## What you have.

The kit lives alongside this file. Read it as a unit; do not invent what it
already defines.

- **`README.md`** · the orientation doc. Read this first, every time. It explains
  the brand intent, the seam, and how the pieces fit.
- **`colors_and_type.css`** · the token contract. Every color, font, radius,
  shadow, motion curve, and semantic class. This is the source of truth. Pull
  values from here with `var(...)`; never hardcode a hex.
- **`preview/*`** · rendered reference pages showing the system assembled
  correctly. Use these to check that your output reads like the kit, not like a
  generic template.
- **`ui_kits/marketing/index.html`** · the marketing component reference:
  buttons, eyebrows, notecards, the collage Cognitive Core, data labels, mastery
  swatches, section rhythm. Copy patterns from here rather than reinventing them.

## Procedure.

1. **Read `README.md` first.** Confirm the surface is a v2 marketing/brand
   surface, not a v1 product surface. If it is product, stop and switch to v1.
2. **Pull tokens from `colors_and_type.css`.** Reference variables by their exact
   names. Do not invent hexes, and do not approximate a token with a literal.
3. **Set a light cream base.** Page base is `--paper-100`; cards are
   `--paper-200`; `--paper-50` for the lightest lift; `--paper-300` dividers,
   `--paper-400` borders. The page is paper, not a screen.
4. **Type the editorial way.** `--font-display` (Fraunces) for H1/H2/H3 display;
   `--font-sans` (Inter) for body and UI; `--font-mono` (JetBrains Mono) for data
   labels, eyebrows, and metadata. Use the defined classes (`.h1`–`.h4`,
   `.body`, `.body-lg`, `.eyebrow`, `.data-label`, `.metadata`, `.mono`).
5. **Reserve color by meaning.** Royal blue (`--signal-500`, `--signal-700` on
   paper) is for DATA and FOCUS only, never decoration. Terracotta
   (`--terracotta-600`/`-500`) is for links, eyebrows, marks, and the italic
   `.display-accent` emphasis. Ochre is warmth. Keep mastery semantics intact:
   emerald high (`--mastery-high-*`), amber/ochre mid (`--mastery-med-*`), rose
   low (`--mastery-low-*`).
6. **Build the signature collage.** The Cognitive Core is assembled from painted
   paper "concept" tiles using the `--swatch-*` palette. Layer `--paper-grain`
   at low opacity with `mix-blend-mode: soft-light` over fills so surfaces read
   as torn, painted paper. It must look hand-assembled, not like flat vector
   shapes.
7. **Use Lucide, never emoji.** Any glyph is inline SVG or a Lucide icon.
8. **One ease curve.** All motion uses `--ease-soft`. Use the paper shadows
   (`--shadow-paper-sm`, `--shadow-paper`, `--shadow-pin`) and the
   `--shadow-signal` focus ring; do not roll your own.
9. **Apply the copy tics.** H2 section headings are sentence case and end with a
   period (the Altera tic). Real Altera copy only: no lorem, numbers with
   sources, the editorial voice.
10. **Use NO em-dashes.** Strict client rule. Use commas, colons, periods, or a
    middot (·). This overrides the old system that mandated em-dashes.
11. **Check against `preview/*` and `ui_kits/marketing/index.html`** before you
    ship. If your output does not feel like those pages, it is wrong.

## When NOT to use.

- **The product app (v1 "Deep Space Lab" dark surfaces).** The logged-in
  experience, the graph workspace, in-app chrome. Those use the v1 dark system.
  Do not pour cream tokens onto them.
- **Any light-on-dark mismatch.** Do not place this kit's ink-on-cream
  components onto a dark v1 background, and do not invert the kit to "fit" a dark
  context. Mixing the two reads as broken, not as range. If a surface needs to
  be dark, it is a v1 surface; route it to the v1 system.

## Things to ask up front.

- Is this a v2 marketing/brand surface or a v1 product surface? (Determines
  which system, full stop.)
- Where does it render: a marketing page, a deck slide, or a social/OG image?
  (Sets safe area, type scale, and aspect ratio.)
- What real Altera numbers and sources back the claims on this surface? (The
  voice is "numbers with sources"; placeholder stats are not allowed.)
- Is there a hero collage to assemble, or does an existing Cognitive Core
  composition get reused?
- Light delivery only, or is there a paired dark v1 surface in the same flow
  that needs a clean handoff at the seam?

## Common mistakes to avoid.

- **Inventing a dark zinc background for v2.** The Reading Room is cream. The
  base is `--paper-100`. There is no dark variant of this kit; if you reach for
  zinc or near-black surfaces, you have drifted into v1.
- **Emoji.** Never. Inline SVG or Lucide only.
- **Em-dashes.** Strict client rule, no exceptions. Use commas, colons, periods,
  or a middot (·).
- **Type below 12px.** Editorial systems breathe. Keep labels and metadata
  legible; do not shrink mono data labels into illegibility.
- **Gradient slop.** No SaaS hero gradients, no glow blooms, no gradient text.
  Color is flat, warm, and reserved. Blue means data, not decoration.
- **Flat-vector collage.** The collage must read as painted, torn paper:
  `--swatch-*` fills with `--paper-grain` layered at low opacity in soft-light.
  If the Cognitive Core looks like clean geometric vector tiles, it has lost the
  signature.
- **Hardcoding hexes.** Always `var(--token)` from `colors_and_type.css`. A raw
  hex in the markup means a token went unused.
- **Forgetting the H2 period.** Section headings (H2) are sentence case and end
  with a period. It is a deliberate Altera tic, not a typo.
- **Misrouting blue or breaking mastery color.** Royal blue is data/focus only.
  Keep emerald high, amber/ochre mid, rose low for mastery; do not recolor them
  for aesthetics.
