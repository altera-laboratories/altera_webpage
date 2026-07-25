# CLAUDE.md — altera_webpage

Static marketing site for Altera Labs (altera-labs.com). No build step: Netlify serves this repo's root directly from `main`. This file is blocked from public serving via a redirect in netlify.toml.

## Deploys cost credits: batch your pushes

- Netlify free credit tier: EVERY push to main triggers a production deploy that draws monthly credits (reset on the 19th). In July 2026, 58 micro-pushes exhausted the month's allowance and froze production deploys.
- Iterate on a work branch, verify on localhost, then merge to main and push ONCE when something is worth shipping. One push = one deploy regardless of how many commits it carries.
- For a main-bound push with no site effect, put `[skip netlify]` in the squash-merge commit subject (that is the PR title, not the branch commits).
- Local preview: `python3 -m http.server 8788` from the repo root, or the Claude Code launch config "site" in `.claude/launch.json`. Port 8787 is often taken by a second session. The live page is /index.html; the v2 design source is /v2/_site.html.

## How work reaches main (as of July 25, 2026)

- Work lands via PR, **squash-merged**. Main's history is one commit per PR: `... (#17)`.
- Because merges are squashed, a merged branch must be **abandoned, not reused**. Reusing it makes the next PR unmergeable ("merge commit cannot be cleanly created"), because the branch still carries commits main now holds as one. Branch fresh from main each time.
- The repo root IS the public site: every tracked file is world-readable. Never commit internal documents here. `.gitignore` guards the known grant/application files; the July 2026 audit found `Blaze_Application.md` had been publicly served, and PR #12 removed it along with `kg_system_audit_prompt.md`, the BII proposal PDF, `/info`, and the loose physics/workflow scratch files.
- `netlify.toml` marks /v2/* and /v1.html `noindex`; they stay reachable for the team but out of search and social previews.

## Design canon

- The v2 "Reading Room" design system is canon: see v2/README.md and v2/SKILL.md.
- Night themes live inside v2/_site.html as a single token-override layer under `html[data-theme]` ("lamplit" | "board"), Day/Lamp/Board toggle bottom-right, `?theme=` deep links. No forked page copies: themes stay in the one source file.
- Hard rules: no em-dashes anywhere, no emoji, mastery encoding stays colorblind-safe (never hue alone), royal blue is reserved for data.
- The Reading Room design is now **live** at index.html (Fraunces headlines, paper ground, terracotta CTA). The archived v1 page is v1.html; branch `v2-live` still holds the original promotion snapshot.
- index.html and v2/_site.html have **diverged** and are maintained separately. index.html is a stack of appended `<style>` layers; v2/_site.html was refactored into four bounded layers (design-tokens / base / responsive / night-themes) plus per-section blocks. Fixes made to one do not reach the other, so port deliberately.
- One trap when porting between them: the mobile menu panel is absolutely positioned, and the two files resolve a *different* containing block (index.html anchors to `.nav-inner`, v2 to `.wrap`). Their left/right offsets are therefore not interchangeable.

## Mobile (<=760px)

- All phone rules live in one layer, `<style id="v2-mobile-nav">`, last in `<head>` so it wins. Keep them there rather than appending new layers.
- The bar is one 64px row: brand, a CTA that appears only after the hero button scrolls away, and a disclosure menu. Section anchors use `scroll-margin-top: 76px` to clear it.
- One `--gutter-m` token (16px) drives the gutter; it is declared *inside* the media block so it does not exist on desktop. Anything needing to sit flush to the screen edge cancels it with `calc(-1 * var(--gutter-m))`, never a hardcoded number.
- `h1.headline em` must stay `display: inline-block`. As a plain inline it splits into two fragments when the emphasised word lands on a line break, which collapses the underline swatch's absolutely positioned `::after` to `width: 0`.
