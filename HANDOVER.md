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

## 2026-07-19 — liability-copy fix (committed LOCAL `10acddf`, ⚠ NOT PUSHED = not live yet)
Killed the penalty-prevention overclaim on two pages (both visible copy AND the JSON-LD FAQ
schema — they duplicate; edit both):
- `markets/india.html`: "SMB OS does the compliance for you" → "handles the tax calculations
  for you".
- `markets/india.html` + `compare/vs-refrens.html`: "one avoided GST filing error (₹50,000
  average) pays for 14 years of it" → "priced far below the ~₹50,000 a single GST filing
  error can cost" (states the stake without promising prevention).
**DELIBERATELY NOT DONE (owner's positioning call):** the full "compliant/compliance" →
"calculation support" reframe — ~70 instances across 11 pages; it IS the site's core
positioning ("GST-compliant invoices", "natively compliant"), so a blanket edit is a
repositioning decision, not a copy fix. If the owner OKs it, do it site-wide in one pass
(visible + JSON-LD + meta descriptions) and re-check `sitemap.xml` untouched.
Pushing deploys these publicly — not yet requested.

Last audit: 2026-07-19 (state = commit `10acddf`, local; remote still at `cdeca51`, 2026-07-10).
