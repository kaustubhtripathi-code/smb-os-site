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
