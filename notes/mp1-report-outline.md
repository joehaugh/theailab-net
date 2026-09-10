# MP1 Report — outline / scaffold

Filename when done: `iphs400_mp1-web-redesign_report_{firstname}-{lastname}_20260910.md`
Length target: 1–2 pages. Markdown.

RULES (from the assignment):
- NOT 100% AI text. This scaffold is bullet points only — you write the prose
  in your own voice. Keep sentences yours; the grade weights this heavily.
- Cover exactly three things: (a) improvements, (b) resources + why, (c) future
  features.

---

## Title line
`IPHS 400 — Mini-Project #1: Web Redesign` / your name / date.
(Confirm in office hours whether he wants a literal title string beyond the
filename.)

## Intro — 2–3 sentences (your voice)
- What the starting point was: the IPHS 400 course shell — static HTML/CSS,
  ~22 pages, one stylesheet derived from WordPress "Twenty Nineteen", a pytest
  suite that checks page structure and links, no live deployment.
- What you set out to do: give it a real visual identity and get it actually
  published.

## (a) Improvements I made
Draw from `notes/mp1-prompts-recovered.md`. Group them:

**Visual redesign**
- Replaced the Twenty-Nineteen-style stylesheet with a new design system
  (css/style.css, ~977 lines reworked).
- Palette: cream ground #f6f5f1, deep petrol accent #0f766e; Instrument Serif
  display + DM Sans body; monospace labels; hairline rules; wide reading
  measure. Modeled on the professor's own site, jonachun.com.
- index.html rebuilt from a plain page into a landing page: hero, course-details
  grid, four mini-projects as cards, course-materials grid.
- Fixed translucent nav bar; restyled body text, tables, code blocks; week
  prev/next navigation; print styles.
- Fonts from Google Fonts with real serif/sans fallback stacks so it degrades
  gracefully offline.
- All 22 content pages updated; the structural hooks the tests rely on left
  intact — `pytest tests/` still 25/25.

**Deployment / infrastructure**
- Added `.github/workflows/deploy-pages.yml`: runs the test suite, then deploys
  to GitHub Pages on every push to main. If a test fails the deploy is skipped
  and the old site stays up.
- Made the workflow enable GitHub Pages itself (via API) so no manual repo-
  settings step was needed.
- Site is now live at https://joehaugh.github.io/theailab-net/
- Documented both the Pages path and the legacy Netlify path in the README.

**Process**
- Did the redesign on a branch, opened PR #1, merged to main.

> Your editing job here: turn these into a few short paragraphs that say what
> YOU judged was wrong with the shell and why these were the right fixes.

## (b) Resources I used and why
- **The pasted design brief** (the ~15k-character "design lead at a small
  studio" prompt) — the primary resource. Say where you got it and why you used
  it: it's a design-standards checklist that steers the AI away from its
  default generic look (cream+serif+terracotta, gradient heroes, Inter, emoji
  markers, everything centered) toward deliberate, subject-specific choices.
- **jonachun.com** — the professor's own site, used as the visual reference for
  palette, typography, and layout language. Why: makes the course site read as
  part of his existing body of work.
- **Claude Code (Sonnet 5)** — the agent that did the implementation: edited the
  CSS and all pages, ran the pytest suite, set up the deploy workflow, drove
  git/gh. Note the division of labor: you set direction and made the
  publish/hosting decisions; the agent executed.
- **GitHub Pages + GitHub Actions** — chosen over Netlify because it's
  zero-config (no account, no secrets) and the repo already had a stalled
  Netlify setup that never had its secrets configured.
- **`git` / `gh` CLI**, **pytest** — tooling.
- The forked class shell: `Avulpix0412/theailab-net`.
- (Add any reference sites / docs / other repos you looked at yourself that
  aren't captured here.)

## (c) Future features I'd add
Ideas to pick from / replace with your own:
- Dark mode (the design brief pushes token-level theming; the current build is
  light only — a real, tested dark theme is the obvious next step).
- A search box or filter across the weekly schedule.
- Pull week/assignment content from Markdown or a data file instead of
  hand-edited HTML per page, so updates are one edit not 22.
- Accessibility pass: focus states, contrast audit, skip-to-content link,
  `prefers-reduced-motion`.
- Add CI checks the shell doesn't have: HTML validation, link-checker on a
  schedule, Lighthouse budget.
- An RSS feed or "recently updated" list so students see what changed.

---

## Submission checklist
- [ ] Confirm with professor: forked from Avulpix0412 OK? report as email
      attachment or committed to repo or both? literal title string?
- [ ] Acknowledge the timing (assignment said Sep 8; it's Sep 10).
- [ ] Report written in your own voice, 1–2 pages, saved with the exact
      filename.
- [ ] Email to jon-chun: repo URL https://github.com/joehaugh/theailab-net,
      report attached, live-site link as a bonus.
- [ ] jon-chun added as collaborator (done) / repo is public (confirmed).
