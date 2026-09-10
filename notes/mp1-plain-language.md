# MP1 — plain-language version of what was done

Same facts as `mp1-report-outline.md`, explained without assuming a coding
background. Technical terms the professor will look for are kept in **bold** and
defined in place — use them in your report, don't strip them out.

---

## The starting point

- The class gave you a **repo** (repository) — a folder of files, tracked by
  **git**, that holds every version of the site. You made a **fork** of it: your
  own copy on your GitHub account that still remembers where it came from.
- The site is a **static site**: plain **HTML** files (the page content and
  structure) and one **CSS** file (**`style.css`** — all the colors, fonts,
  spacing, layout). "Static" means there's no server doing work and no
  **JavaScript** — what's in the files is exactly what the visitor sees.
- The original CSS was adapted from **"Twenty Nineteen,"** a stock **WordPress**
  theme. So it worked, but it looked like a default blog, not like a designed
  course site.
- The repo also has a **test suite** written with **pytest** (a Python testing
  tool). These **tests** are small automated checks that open each page and
  confirm things like "every required section is present" and "no links are
  broken." If a test **fails**, something is wrong.
- Nothing was **deployed** — "deployed" means published to a public web address.
  The files existed on GitHub but there was no actual website you could visit.

## What "the redesign" actually changed

- **Rewrote the stylesheet.** Almost all of `style.css` was replaced (about 977
  lines touched). Nothing about the page *content* changed here — only how it
  looks.
- **Defined a design system** instead of picking colors ad hoc. A **design
  system** = a fixed, named set of choices reused everywhere:
  - **Palette** (the set of colors): a cream background (**hex** code
    `#f6f5f1` — hex is just how colors are written in code) and a dark
    teal/green accent (`#0f766e`) for links and highlights.
  - **Typography** (the fonts and how text is sized): a display **typeface**
    called *Instrument Serif* for headings, *DM Sans* for body text, and a
    **monospace** font (fixed-width, typewriter-style) for small labels.
  - Thin divider lines ("**hairline rules**"), a comfortable line length for
    reading, consistent spacing.
  - All of this was modeled on **jonachun.com**, the professor's own website, so
    the course site looks like part of his existing work.
- **Rebuilt the home page (`index.html`).** It went from a plain page to a
  proper **landing page**: a **hero** (the large headline area at the top), a
  grid of course details, the four mini-projects shown as **cards** (boxed
  summaries), and a grid of course-materials links.
- **Restyled everything else:** the **navigation bar** (the menu at the top —
  made it a fixed, slightly see-through strip), body text, **tables**, code
  blocks, the "previous / next week" links, and a **print stylesheet** (how the
  page looks if someone prints it).
- **Fonts load from Google Fonts** (a free font-hosting service) with a
  **fallback stack** — a list of backup fonts the browser uses if the real one
  can't load, so the page still reads fine offline.
- **All ~22 pages updated**, and the **structural hooks** the tests check for
  (specific labels in the HTML the test suite looks for) were left untouched —
  so **`pytest tests/` still passes 25 out of 25**.

## Getting it actually published

- Set up **GitHub Pages** — a free service that turns a GitHub repo into a live
  website. The address is `https://joehaugh.github.io/theailab-net/`.
- Wrote a **workflow** — a file (`deploy-pages.yml`) that tells **GitHub
  Actions** (GitHub's automation system) what to do automatically. This one
  says: every time code is pushed to the main version of the site, first **run
  the tests**; if they pass, **deploy** the site; if any test fails, skip the
  deploy so the broken version never goes live.
- Normally you have to flip a setting in the repo by hand to turn Pages on. That
  step kept not working, so the workflow was changed to **enable Pages itself**
  through GitHub's **API** (the programmatic way software talks to GitHub). Now
  there's no manual setup step at all.
- The repo already had a half-finished setup for a different host, **Netlify**,
  that was never completed (it needed secret keys that were never added).
  GitHub Pages was chosen instead because it needs no account and no keys. Both
  options are written up in the **README** (the repo's front-page documentation
  file).

## How the work was organized (git terms)

- Changes were made on a **branch** — a separate line of edits that doesn't
  touch the live version until you're ready.
- The branch was opened as a **pull request** (**PR #1**) — a formal "here are
  my changes, review them" request.
- Then it was **merged** — folded into the **main** branch, which is what
  GitHub Pages publishes.
- Each saved step is a **commit** (a snapshot with a message describing it).

## Who did what (for section b, the honesty part)

- **You** set the direction (the design brief, "make it match his site"), made
  the hosting decision (Pages vs. Netlify), and did the GitHub click-steps.
- **Claude Code** (an **AI coding agent** — an AI that can read and edit files,
  run commands, and use git on your machine) did the implementation: edited the
  CSS and all the pages, ran the test suite, wrote the deploy workflow, and ran
  the git commands.
- The big **prompt** you pasted in was a **design brief / design-standards
  checklist**: a long set of rules that pushes an AI away from its generic
  default look and toward deliberate, subject-specific design.
