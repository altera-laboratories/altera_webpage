# Altera Labs Landing Page — AI-Slop Design Audit

**Slopness Index: 38 / 100**  *(honest band: 35–44)*
**Reads as:** recognizably in-genre, competently hand-built — **not slop.**

Audited against the 47-subreddit "vibe-coded design tells" corpus. Method: one analyst
per tell dug `index.html` for exact-token evidence (hex codes, class names, fonts, line
numbers); an adversarial verifier re-checked each finding against the file (guarding
hard against the classic "called blue purple" false positive); a synthesizer produced
the weighted score. 25 agents total. Run against the live deployed `index.html`
(commit `17106df`).

## How the score was computed
Each tell carries a Reddit-derived prevalence **weight** (share of on-topic comments)
and an adversarially-**verified** severity (0 = actively avoids the tell, 10 = textbook
worst case).

- **Specific tells only** (weight-sum 10.85): weighted-avg severity 3.17/10 → **32/100**.
- **Including the umbrella "looks like AI" verdict** (weight 5, severity 7): → **44/100**.
- **Published: 38** — between the two. The umbrella's 7 measures "exhibits the canonical
  markers," not "is indistinguishable from slop," and folding it in at full weight
  double-counts the silhouette (its markers already appear as Tells #1/#5/#6/#9/#10).

## Scorecard

| Tell | Weight | Severity /10 | One-line verdict |
|---|---|---|---|
| UMBRELLA: "looks like AI slop" | 5.0 | 7 | Hits ~9/10 genre markers, but real photos, bespoke D3 graph, KaTeX, off-default blue + zero gradient text cap it at 7. |
| #1 Default shadcn/Tailwind kit | 2.5 | 4 | Hand-written Tailwind that *reads* in-genre (zinc cards, py-24/p-10 rhythm) but re-tokenized blue + bespoke cards prove it's not the untouched kit. |
| #2 The "AI purple" | 2.3 | 1 | Deliberately dodged — sole accent is true blue; the one purple is a quarantined D3 data color, never chrome. |
| #3 Gradients / gradient hero text | 2.0 | 1 | The single most-mocked tell is absent: flat white H1, zero `bg-clip-text`, all gradients monochrome/low-alpha. |
| #4 Too many hover & scroll animations | 1.1 | 6 | Polished but busy multi-system motion stack; tasteful easing + hover-gating, but **no `prefers-reduced-motion` guard**. |
| #5 Rounded corners on everything | 0.8 | 6 | Universal rounding, 9999px pill CTAs, zero sharp surfaces — but a documented 4-tier radius scale shows intent. |
| #6 Dark mode with neon glow | 0.7 | 5 | Forced-dark + full glow toolkit, executed with restraint (low opacity, data-viz-justified bloom). |
| #7 Emoji as icons/bullets | 0.5 | 0 | Fully clean — real Lucide icon kit + inline SVGs; zero emoji anywhere. |
| #8 Generic sans (Inter) | 0.4 | 8 | Near-textbook: Inter is body + every display heading; no typeface with a point of view. |
| #9 Symmetric hero + 3 cards | 0.4 | 3 | Centered dual-CTA hero is textbook, but everything below is the prescribed antidote (asymmetric 2-col, 8/4 bento, tilted mockups). |
| #10 Bento grids (contested) | 0.1 | 6 | Self-labeled 12-col 8/4 bento, but confined to one section with substantive (non-lorem) tiles. |
| Bonus: mesh/aurora/blob backgrounds | 0.05 | 3 | Blur orbs present but single-hue, ultra-low-alpha, behind content — atmosphere, not rainbow mesh. |

## On-sight verdict
**Not badly. You're in the genre, but you are not slop.** A 5-second squint reads
"modern AI-SaaS landing page" — you hit ~9 of 10 silhouette markers (dark zinc base,
one blue accent, glass bento cards, pill CTAs, glow, scroll-reveal, tilted mockups,
Inter). But 30 seconds of looking finds the things templates can't fake: a real D3
knowledge graph, a live KaTeX Beta-BKT mastery equation, real headshots, real named
partners (JHU/NVIDIA/Google Cloud/Canvas), an off-default periwinkle accent, a
documented in-file design system — and **none of the three most-mocked tells** (no
AI-purple, no gradient hero text, no emoji icons). The slop signal is **silhouette,
not substance.**

## What it deliberately DODGES (credit where due)
- **NOT purple.** Sole accent is a genuine 225° royal blue `#476ee3` (hand-named, not
  Tailwind `blue-500`/indigo). The one true purple `#a855f7` is quarantined as 1 of 7
  categorical D3 edge colors — never UI/brand chrome. Verifiers repeatedly caught and
  rejected the "this is purple" false positive.
- **NO gradient hero text.** Flat solid-white H1. `bg-clip-text` / `text-transparent`
  return zero matches in the whole file. This is the single most-named AI tell, and
  it's categorically absent.
- **NO emoji icons.** Real Lucide vector kit (18 instances) + inline SVGs. Bullets are
  CSS gradient dots, not glyphs.
- **Varied, asymmetric layout below the hero** — two asymmetric `md:grid-cols-2 gap-20`
  sections, an 8/4 bento, tilted mockups. NOT three equal feature cards (the only
  `grid-cols-3` is the team headshot grid).

## What it genuinely CONFORMS to (the real tells)
- **Inter as the only voice (sev 8).** Body and every display heading. Highest-severity
  finding. No heading typeface with a point of view anywhere.
- **Animation-heavy (sev 6).** Hero fade, scroll-reveal, card lift, mousemove parallax,
  button glow, 12 hover-zooms, 6 pulse loops, a ping, full D3 interactivity. Mitigated
  by tasteful easing/gating — but **no `prefers-reduced-motion` guard** (a real a11y gap).
- **Rounded-everything (sev 6).** 59 `rounded-full`, 9999px pill CTAs, `rounded-3xl`
  cards; zero sharp surfaces. Mitigated by a documented 4-tier radius scale.
- **Dark + neon glow (sev 5).** Forced-dark, no toggle, full glow toolkit. Mitigated by
  low opacities and an author "reduced for cleaner look" comment.
- **Kit-feel rhythm (sev 4).** Uniform `py-24` / `p-10` / `gap-8` + heavy zinc dark-card
  surfaces read in-genre even though the code is hand-written (zero shadcn/React signatures).

## Recommended fixes (ranked by ROI, mapped to the writeup's own prescriptions)
1. **Swap Inter for a display face on headings** *(prescription: "swap Inter")* —
   highest-severity tell (8), cheapest structural fix (~1 hr). Keep Inter for body/UI;
   give H1/H2 a face with character. One `font-display` token on `h1,h2` flips your most
   identity-defining type off the genre default.
2. **Nudge the accent off the default-blue family / add a real secondary hue**
   *(prescription: "move palette off the default")* — blue-on-zinc is the genre's home
   turf; a teal-leaning shift or promoting emerald/amber into marketing chrome breaks the
   monochromatic-blue silhouette. Token-level, 1–3 hrs.
3. **Add a `prefers-reduced-motion` guard** — the one correctness/accessibility miss the
   verifiers flagged. One media query, ~30 min.
4. **Feed a real (non-SaaS) reference site into a visual pass** *(prescription: "feed a
   real reference site")* — highest ceiling for shedding genre resemblance, but it's a
   design pass, not a code change. High effort; defer unless pushing below 30.

**Protect, don't touch:** the D3 graph, the KaTeX equation, the real photos/partners,
and the documented design system. These are why you're a 38 and not a 70.
