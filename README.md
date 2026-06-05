# tapesim-website

Static marketing site for **TapeSim** (tapesim.app). Plain HTML/CSS — no build
step, no framework. Hosted on GitHub Pages.

## Pages

- `index.html` — landing (hero, features, how-it-works, pricing)
- `download.html` — downloads + license activation instructions
- `docs.html` + `docs/*.md` — user documentation. The HTML is a thin shell; the
  pages are Markdown rendered client-side by `marked` (CDN, SRI-pinned). The sidebar
  order + valid page slugs live in the `PAGES` array inside `docs.html`; add a page
  by dropping a `docs/<slug>.md` and adding `{ slug, title }` to that array.
- `terms.html`, `privacy.html`, `refund.html` — legal (the payment provider expects these)
- `styles.css` — shared styles (palette mirrors the desktop app)
- `CNAME` — custom domain (`tapesim.app`)
- `.nojekyll` — serve files as-is, skip Jekyll processing

## Status

The site is **live at https://tapesim.app** (HTTPS enforced). TapeSim sells as a
**€50/mo subscription with a 7-day free trial** via **Polar** (Merchant of Record).
After checkout the buyer's license key appears in their Polar customer portal
(linked from the receipt email); the trial means no charge until day 8, cancel
before then to pay nothing. The trial is the try-before-you-buy — no beta keys.

> Payments moved from Lemon Squeezy to **Polar** (2026-06-05) after LS rejected the
> store. Polar is also an MoR (handles EU VAT), has a client-callable license API
> (no server, no secret), and a customer portal where buyers self-serve their key +
> manage activations. The desktop client talks to Polar directly — see
> `tapesim/TapeSim.Ui/Polar.fs`. Sandbox vs production is just the API base + org id;
> shipped (Release) builds are hardcoded to production.

- **Downloads** — the `download.html` cards point at the GitHub Release assets on
  this repo (`Setup.exe`, portable `.zip`, Linux `.zip`). Releases are produced by
  the app repo's `scripts/publish.ps1`, which also bumps these links.
- **Checkout** — the "Start a free trial" buttons (`index.html`, `download.html`)
  link to the Polar checkout (`buy.polar.sh/...`). Live as soon as Polar approves
  the store in onboarding review.
- **Support** — `support@tapesim.app` (a dedicated Fastmail mailbox).
- **Legal** — `terms.html` / `privacy.html` / `refund.html` are filled for personal
  ownership (Marko Grdinić, Croatia — sole proprietorship until revenue justifies an
  obrt). Refund policy: no refunds after the 7-day trial.

## Deploy (GitHub Pages)

Already set up — pushes to `main` auto-deploy. Recorded here for reference:

- **Source:** Settings → Pages → Deploy from a branch, `main`, `/ (root)`.
- **DNS** (at Cloudflare): apex `tapesim.app` → A records `185.199.108.153`,
  `185.199.109.153`, `185.199.110.153`, `185.199.111.153`; `www` → CNAME
  `mrakgr.github.io`. All **DNS-only** (grey cloud). The `CNAME` file pins the
  custom domain — don't delete it (doing so drops the domain).
- **HTTPS:** Enforce HTTPS is on (Let's Encrypt, auto-renewed).
- **Mail** is separate: `tapesim.app` MX points at Fastmail; the website A/CNAME
  records are independent, so never touch the MX/SPF/DKIM records when editing the
  site DNS.

## Local preview

Run a static server from this dir and open `http://localhost:8001`:

```
python3 -m http.server 8001
```

**The docs page must be served over HTTP, not opened as a `file://` URL.** `docs.html`
fetches its Markdown at runtime, and browsers block `fetch()` of local files under
`file://` (same-origin policy) — you'll get "Couldn't load this page." The plain HTML
pages open fine either way; only the docs need the server. GitHub Pages serves over
HTTPS, so this only affects local preview.
