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

Last audit: 2026-07-12 (state = last commit `cdeca51`, 2026-07-10).
