# IPHS 400 — Mini-Project #1: Web Redesign

**Joe Haugh** · September 10, 2026

Live site: https://joehaugh.github.io/theailab-net/
Repo: https://github.com/joehaugh/theailab-net

*Note on timing: the assignment listed a due date of Thursday, Sep 8. This is
being submitted Sep 10 — apologies for the delay.*

---

To begin this project I began looking at various websites that had a clean look
and have dedicated pages to different options. I envisioned a website where I
could quickly click over to the schedule, syllabus, any assignments, and find
the class policy. Eventually I decided to model the page off of your personal
site, Jonachun.com. I brought this and the instructions, and the forked site
with all the files into my claude code and began to run and see what it would
look like. Currently it shows that I forked from "Avulpix0412" instead of
"Jon-chun" but this is because I went to the specific "Ailab" folder and forked
it from there. I prompted claude to replace the old stylesheet from the
wordpress theme to make the new design a cream background, teal accent, and
Instrument Serif headings over DM Sans body that matches your website. I rebuilt
the landing page to have the four mini-projects as cards. This gave it a clean
way to access each project. Then I prompted Claude to have specific pages for
each of the sections, "syllabus, schedule, assignments, policy, and about", on
its first attempt I could not access the specific pages, so I kept reworking the
prompts until I could click and access each page. We ended up running tests on
all pages to make sure they worked.

The next phase was publishing the work on GitHub, which I found to be the
hardest part of the process. The original redesign was done on a branch, opened
as a pull request, then merged into main. In order to make it a live site I used
GitHub Pages. The repo already had a half-finished Netlify setup, but it could
not be configured, so Pages was the easier path. Then I added a GitHub Actions
workflow. From here is where I kept having trouble. I had to flip a setting to
allow the page to deploy but I kept getting a red X every time I changed the
setting. The workflow was rewritten so it enables Pages itself through GitHub's
API so no manual change in settings was needed and the deploy ran green. The
site is now live at https://joehaugh.github.io/theailab-net/ with no login
needed. I originally thought this became my personal site, however it is a
project site hosted by GitHub.

For future improvements to the website I want to give students options. By this
I mean we can easily add dark mode that would keep a good aesthetic for the
site. I also believe the cards for the mini-projects allow a great way to
showcase past mini-projects so students can be inspired by their peers' work and
it will help them generate ideas for future projects. On a more technical side,
right now every page is hand-written HTML and the 15 week pages are all
near-duplicates. I would move the content into data files and add a build script
that generates the HTML pages from templates. This improves the site by removing
a class of bugs on the site (the 15 week pages share the same header, nav, and
prev/next links, and nothing stops them from drifting out of sync when you edit
one and not the others; generated-from-a-template pages can't drift). This step
would also allow for easier implementation of future changes to the site.
