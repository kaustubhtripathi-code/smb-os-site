# HANDOVER — smb-os-site

SEO/marketing site for **SMB OS** (the smb-variants invoicing module inside
`OneDrive\Desktop\freelanceros` — read its CLAUDE.md checkpoint for product state).
`index.html` + comparison pages (vs Zoho / Wave / Refrens) + `sitemap.xml` + `robots.txt`.

- Repo: `kaustubhtripathi-code/smb-os-site` · GitHub Pages, LIVE since 2026-07-10.
- Redeploy = push to default branch. Keep `sitemap.xml` updated when adding pages.
- **Fact-check discipline (established `cdeca51`):** competitor claims were hand-verified —
  precise Wave pricing, correct Zoho M-Pesa/PayFast cells, "not advertised" phrasing for
  absence claims. Any comparison edit must cite a checkable source; never assert a
  competitor LACKS a feature without the "not advertised" hedge.
- Product truth constraint: the free tier is 10 invoices/month (enforced in the app since
  07-10, `shared/lib/quota.ts`) — site claims must match.
- Pro waitlist address used at cap: hello@smbos.app (no billing exists yet).
- User steps: none pending for the site; payments go-live is blocked on provider creds in
  the product (.env — Stripe/Flutterwave/M-Pesa/PayFast/GSP).

## 2026-07-19 — liability-copy fix (`10acddf`, PUSHED same day = LIVE on Pages)
Killed the penalty-prevention overclaim on two pages (both visible copy AND the JSON-LD FAQ
schema — they duplicate; edit both):
- `markets/india.html`: "SMB OS does the compliance for you" → "handles the tax calculations
  for you".
- `markets/india.html` + `compare/vs-refrens.html`: "one avoided GST filing error (₹50,000
  average) pays for 14 years of it" → "priced far below the ~₹50,000 a single GST filing
  error can cost" (states the stake without promising prevention).
**FULL REFRAME DONE same day (`538f58e`, owner said "build whatever is left"; PUSHED = LIVE):**
site-wide pass over all 11 pages (visible copy + JSON-LD + titles/meta/OG). Rule applied —
**product-delivers-compliance claims** rewritten to what's true (fields/format/calculations:
"natively compliant"→"built for the tax rules", "actually compliant"→"GST's actual rules
built in", "X-compliant invoices"→"X-required format", "Compliant, not scary"→"Tax math,
not scary" + dropped "No penalties", CTAs "compliant invoice"→"tax-ready invoice",
homepage nav/kickers "Compliance"→"The output"/"Real tax artifacts", compare tables
"native tax compliance"→"native tax-rule support", Refrens "focused invoicing tool:
compliance,…"→"…: the right tax fields and calculations,…"); **kept** legal-education
copy (what the law requires an invoice to contain), "Compliance FAQ" topic labels,
competitor facts and market stats. Verified: zero remaining product-compliance claims
(grep audit), no mojibake (use .NET UTF8 read/write or the Edit tool — PS5.1
Get/Set-Content re-encodes em-dashes), deploy verified live on Pages.

Last audit: 2026-07-19 (state = pushed through 2026-07-19).

## 2026-07-25 responsive pass
Mobile nav no longer deleted at <=760px — the five nav links collapse into a `<details>`
hamburger (zero JS; `order:3` puts it at the right edge so the drop-down can't escape the
viewport). Added `color-scheme:dark`. Verified: 0 horizontal overflow and 50px tap targets
at 375px; nav renders as a normal horizontal row at 820 / 1280.
The `compare/` tables are wider than a phone by design and scroll inside their own
`overflow-x:auto` container — the page itself does not scroll sideways. That is correct;
do not "fix" it by shrinking the table.


## 2026-09-07 — Local HTML repair (not deployed)
Astra portfolio review restored the complete sibling favicon tag in compare/index.html:16 and markets/index.html:16. Previously the unclosed href absorbed the following canonical tag. Two HTML line replacements, uncommitted. Regression failed before and passed after for all 11 site pages; byte identity with compare/vs-wave.html verified. Runnable check: C:/Users/91851/Documents/Codex/GPT 6 Astra/audits/2026-09-07-project-review/repair_smb.py. No push or browser rendering validation.


## 2026-09-07 — Tested release and targeted recovery

This supersedes the earlier local-only status for the HTML repair. Code commit: `1ab2597`; pre-change main: `f92d583`. Changed pages: compare/index.html, markets/index.html. Fixes malformed favicon attributes which consumed following HTML. No application backend or data changed.

Verification: stdlib HTML regression check; browser inspection of all five repaired pages across the two sites confirmed stylesheets and expected headings. SMB canonical links parse independently; Everfold product CSS applies. AI OS screenshot visually checked. Run `python scripts/check_html.py` from this repository. This is a targeted markup check, not a full accessibility or product audit.

Deployment: existing GitHub Pages source is `main`, repository root. Push triggers the existing deployment. Consult the subsequent release receipt for actual remote/build/live verification; a commit alone does not prove deployment.

### Rollback by symptom

| Symptom | Action | Scope and caution |
| --- | --- | --- |
| New regression isolated to these repaired pages | From a clean, up-to-date main, `git revert 1ab2597`, rerun the check, then `git push origin main` to publish the reversal. | Reverts only the HTML repair; documentation/checks and unrelated commits remain. **The old markup is known broken**, so the regression check should reject that reversal. Prefer a small corrective fix; do not publish the known-broken reversal simply because it exists. |
| Only one page regressed | Inspect `git show 1ab2597 -- path/to/affected/page`; apply only that hunk in reverse to that page, inspect `git diff`, test and commit it. | Do not restore the entire repository or another product. Reversing the favicon repair reinstates the original defect; a corrected favicon or removal of only its link is safer. |
| Pages deployment fails or old page remains visible | Check GitHub Pages latest build SHA/status and compare remote main. Retry the existing build after diagnosing failure. | No reason to roll back code when the new build never went live. Avoid force-pushing. |
| Regression only in the new check/documentation | Revert the documentation/check commit found with `git log -- scripts/check_html.py HANDOVER.md`. | Keep `1ab2597`; this leaves the working website repair intact. |
| App login, saved data, API, video or unrelated product breaks | Investigate that application's own deployment and handover. | These static favicon repairs changed no app code, media or database. No data restore is appropriate. |

Before any reversal, preserve uncommitted work and inspect later changes. After a forward fix or rollback, rerun the local check, check the affected page in a browser, push without force, and confirm the Pages build SHA and live page. Never restore a database for this change.
