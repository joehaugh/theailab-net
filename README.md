# IPHS 400: Frontiers in AI

**Kenyon College — Integrated Program for Humane Studies (IPHS) — Fall 2026**

Course website for IPHS 400, a hands-on study of AI software engineering (AI-SWE):
configuring, extending, and orchestrating AI coding agents through a professional
software development lifecycle. This repository contains the site's source and
its test suite; course submissions, quizzes, and grades are handled separately
on Moodle.

- **Instructor:** Jon Chun
- **Schedule:** Tu/Th, 2:40–4:00 PM · Timberlake #5 (Evans Conference Room)
- **Live site:** _add Netlify URL here once deployed_

## Repository Structure

```
.
├── index.html              # Home page
├── 404.html                 # Not-found page
├── core/                    # Syllabus, schedule, assignments, policies, about
│   ├── syllabus.html
│   ├── schedule.html
│   ├── assignments.html
│   ├── policies.html
│   └── about.html
├── weeks/                   # One page per week, week-01.html … week-15.html
├── css/
│   └── style.css            # Single shared stylesheet, no build step
├── tests/                   # pytest suite validating the site
│   ├── conftest.py
│   ├── test_unit_html_structure.py
│   ├── test_integration_links.py
│   ├── test_e2e_site.py
│   └── requirements.txt
└── .github/workflows/       # CI: deploy to Netlify on push to main
```

The site is static HTML/CSS with no build step or JS framework. Every page
shares one stylesheet and a common header/nav/hero/footer skeleton.

## Local Development

Serve the site locally with Python's built-in HTTP server:

```bash
python3 -m http.server 8080
# then open http://localhost:8080/
```

No install step is required to view the site — only the test suite has
dependencies.

## Running the Tests

The test suite (pytest + BeautifulSoup/lxml) validates structural and content
integrity of every page:

- `test_unit_html_structure.py` — every page has a DOCTYPE, title, stylesheet
  link, header, footer, and hero `<h1>`; no leftover template branding; no
  placeholder or stub content
- `test_integration_links.py` — every internal link resolves; navigation is
  identical across all pages; the schedule links to all 15 week pages
- `test_e2e_site.py` — required files/directories exist; exact page count;
  every page is reachable from `index.html` (no orphaned pages)

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r tests/requirements.txt
pytest tests/ -v
```

Run a single test file or test:

```bash
pytest tests/test_unit_html_structure.py -v
pytest tests/test_integration_links.py::TestNavConsistency::test_nav_links_resolve -v
```

## Deployment

### GitHub Pages (no configuration required)

[`.github/workflows/deploy-pages.yml`](.github/workflows/deploy-pages.yml)
runs the test suite and then publishes the repository root to GitHub Pages on
every push to `main`. The workflow enables Pages itself
(`actions/configure-pages` with `enablement: true`), so no manual
**Settings → Pages** step is needed. The site serves at
`https://<owner>.github.io/theailab-net/`, and Pages serves `404.html`
automatically for unknown paths. Deployment can also be triggered manually
from the Actions tab (`workflow_dispatch`).

### Netlify (optional alternative)

[`.github/workflows/deploy-netlify.yml`](.github/workflows/deploy-netlify.yml)
publishes the same root to Netlify on push to `main`. It requires two
repository secrets under **Settings → Secrets and variables → Actions**:

| Secret | Description |
|---|---|
| `NETLIFY_AUTH_TOKEN` | A Netlify personal access token |
| `NETLIFY_SITE_ID` | The target Netlify site's API ID |

Until those secrets are configured this workflow fails at the deploy step. If
you deploy via Pages, you can delete `deploy-netlify.yml` and `netlify.toml`.

## Content Source and Provenance

All course content (syllabus text, schedule, assignments, policies) is
sourced from the official Fall 2026 syllabus. The visual system — cream
ground, deep petrol accent, Instrument Serif display type over DM Sans,
hairline rules and a wide reading measure — is adapted from the instructor's
site, [jonachun.com](https://jonachun.com/), for visual consistency across
Jon Chun's Kenyon web presence; no content from that site is reused here.
Web fonts load from Google Fonts with a serif/sans fallback stack, so the
site still reads correctly offline or if the CDN is blocked.

## License

See [LICENSE](LICENSE).
