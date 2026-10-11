# AGENTS.md — smb-os-site

Public SEO/marketing site for **SMB OS**, the small-business invoicing module of the owner's
FreelancerOS product (the app itself lives in a separate repo). Homepage, competitor
comparison pages and per-market pages. Live on GitHub Pages since 2026-07-10. **PUBLIC repo.**

## Stack & layout
Plain static HTML/CSS, no build step.
- `index.html`: homepage; `market.css`: shared stylesheet for market pages
- `compare/`: `index.html`, `vs-refrens.html`, `vs-wave.html`, `vs-zoho-invoice.html`
- `markets/`: `index.html`, `india.html`, `kenya.html`, `nigeria.html`, `south-africa.html`, `usa.html`
- `sitemap.xml`, `robots.txt`, `.nojekyll`, `assets/`
- `ci/site_check.py` (CI link/asset checker + stager), `scripts/check_html.py` (malformed-tag regression check)

## Setup
None. Needs `python3` (3.12+) and `node` (checker runs `node --check` on any JS files).

## Run / build / test / lint
- Preview: `python3 -m http.server 8000` (unverified)
- Checks (exactly what CI runs; stage outside the repo so no `_site/` is created):
  - `python3 ci/site_check.py --repo smb-os-site --output /tmp/smb-os-site-_site` (verified 2026-10-11)
  - `python3 scripts/check_html.py` (verified 2026-10-11)
  - `site_check.py` refuses an existing output dir; delete it before re-running. Never commit `_site/`.

## Environment variables
None required.

## Codex cloud environment
- Setup script: `python3 --version && node --version` (nothing to install)
- Internet during agent phase: off is fine for edits/checks; fact-checking competitor claims needs web access
- Secrets to add: none

## Deployment (do not break)
- GitHub Pages, default branch `main`. `.github/workflows/ci-cd.yml` checks every push/PR and
  deploys with `actions/deploy-pages` only from `main`. A push to `main` = live. Do not push to
  `main` without owner approval; use a branch + PR. Do not edit the workflow or `ci/` unless asked.
- Keep `sitemap.xml` updated when adding pages. Keep `.nojekyll`.

## Rules for agents
- **Fact-check discipline:** competitor claims (Wave pricing, Zoho M-Pesa/PayFast cells, etc.)
  were hand-verified. Any comparison edit must cite a checkable source. Never assert a
  competitor lacks a feature without the "not advertised" hedge.
- **No product-delivers-compliance claims.** Say "built for the tax rules", "tax-ready
  invoice", "X-required format", "handles the tax calculations". Do not say "compliant
  invoices", "does the compliance for you", "no penalties" or promise to prevent filing errors.
  Legal-education copy (what the law requires) and "Compliance FAQ" labels are fine.
- Visible FAQ copy and the JSON-LD FAQ schema duplicate each other: edit both. Also check titles/meta/OG.
- Product truth: free tier is **10 invoices/month** (enforced in the app); site claims must match.
  No billing exists yet; Pro waitlist address at cap is hello@smbos.app.
- Preserve UTF-8 (em dashes, rupee signs): edit with tools that do not re-encode files.
- `compare/` tables are intentionally wider than a phone and scroll inside their own
  `overflow-x:auto` container; do not "fix" by shrinking them. Mobile nav is a zero-JS `<details>` hamburger.

## Open work
- None for the site. `ci/portfolio-20260907` is already merged into `main`. Payments go-live
  is blocked in the product repo, not here. Full history in `HANDOVER.md`.
