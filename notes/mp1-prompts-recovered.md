# MP1 — Recovered record of the website redesign work

Reconstructed from local Claude Code session transcripts on this machine
(sessions of 2026-09-01 through 2026-09-03). Raw material for the MP1 report,
section (b): "what resources you used (specific prompts...) and why."

## Sessions involved

- `924317ed` (Sep 1) — environment setup: created `~/code/`, installed `git`
  and `gh`, cloned `https://github.com/joehaugh/theailab-net`.
- `14640834` (Sep 1–3) — the actual redesign, PR, and deployment. Main session.
- `a8c0a09f` (Sep 8) — asked Claude, on the professor's instruction, for "the
  best methods for going about" a website-shell redesign (project already done).

## The prompts you actually gave (verbatim, in order)

1. "the repo url is 'https://github.com/joehaugh/theailab-net' lets vibe code to
   make it better"

2. A long pasted design-direction brief (~15,300 characters). It opens:
   "Approach this as the design lead at a small studio known for their
   versatility, giving every client a visual identity pitched at the treatment
   the task actually calls for. Make deliberate choices about palette,
   typography, and layout that are specific to this subject, and avoid templated
   designs. ## Read the request first ..."
   It covers: calibrating treatment vs. over-designing; honoring an existing
   design system; typeface pairing and type scale; loading libraries from CDN
   rather than pasting; choosing intentional neutrals; designing light/dark
   themes at the token level; layout via flex/grid gap; composing repeated
   components consistently; charts drawn to scale; showing the page at rest;
   avoiding the current "AI-generated design" clichés (warm cream + serif +
   terracotta, acid-green pop on near-black, purple-blue gradient hero, Inter/
   Space Grotesk, emoji section markers, everything centered, rounded-lg
   everywhere); clean HTML/CSS build hygiene; product-style page titles;
   meaningful structure over decoration; and a "sketch a token system (color/
   type/layout), build once, look once, publish" process.
   [Full text saved separately if needed — retrievable via `claude --resume` on
   session 14640834 in `~/code/theailab-net`.]

3. Follow-up logistics questions (not design): "So is the final output you gave
   me its own website or its just on my github?"; "could someone click on my
   github and then find a link to the claude.ai site that claude hosts?";
   "would it be difficult for you to remove the preview link?"; "how come when I
   click on the link i get this screen" (404); "Give me a simpler step by step";
   "There is an error the x is red..."

## What was built (from Claude's own summary + git history)

Commit `be1a406` "Redesign site on the jonachun.com editorial system" —
24 files changed, 703 insertions / 538 deletions:

- **New visual system**, modeled on the professor's own site jonachun.com:
  cream ground `#f6f5f1`, deep petrol accent `#0f766e`, Instrument Serif
  display face over DM Sans body, monospace labels, hairline rules, wide
  reading measure — an "editorial field-notebook" look.
- `css/style.css` almost entirely rewritten (977 lines touched) — replacing the
  old WordPress "Twenty Nineteen"-derived stylesheet.
- `index.html` (+99 lines) turned into a real landing page: hero, course-details
  credential grid, the four mini-projects as a card grid, course-materials grid.
- Fixed translucent nav bar; restyled prose, tables, code blocks; week
  prev/next navigation; print styles.
- Fonts served from Google Fonts with serif/sans fallback stacks (readable
  offline).
- All 22 content pages updated; structural hooks the pytest suite checks were
  left intact — `pytest tests/` → 25 passed.

Commit `3fb6637` "Add GitHub Pages deploy workflow" — new
`.github/workflows/deploy-pages.yml`: runs the test suite, then deploys to
GitHub Pages on every push to `main`; README updated to document Pages and the
legacy Netlify path.

Commit `1a27bbf` "Let the Pages workflow enable Pages itself" — workflow amended
to enable Pages via the API so no manual Settings change was needed.

PR #1 (`redesign-jonachun-editorial`) merged to `main` (`bc1cd77`).

Live result: https://joehaugh.github.io/theailab-net/

## Notes for writing section (b) honestly

- The single biggest "resource" was the pasted design brief (prompt #2). Worth
  saying where it came from and why you used it — it's essentially a
  design-standards checklist that pushed the output away from generic
  AI-site defaults toward something matched to the professor's own site.
- Reference site used as the visual target: **jonachun.com** (the professor's
  site) — palette, typography, and layout language were derived from it.
- Base repo: forked from `Avulpix0412/theailab-net` (the class shell).
- Tooling: `git`, `gh` CLI, GitHub Pages + GitHub Actions, pytest.
