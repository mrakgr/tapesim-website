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
- `terms.html`, `privacy.html`, `refund.html` — legal (Lemon Squeezy expects these)
- `styles.css` — shared styles (palette mirrors the desktop app)
- `CNAME` — custom domain (`tapesim.app`)
- `.nojekyll` — serve files as-is, skip Jekyll processing

## Status

The site is **live at https://tapesim.app** (HTTPS enforced). TapeSim is in
**beta**: checkout currently runs on Lemon Squeezy **test mode**, so no real
charge is made — the download page explains the test card. Going to real
payments is a Lemon Squeezy dashboard flip + swapping the checkout URLs below;
no other site change.

- **Downloads** — the `download.html` cards point at the GitHub Release assets on
  this repo (`Setup.exe`, portable `.zip`, Linux `.zip`). Releases are produced by
  the app repo's `scripts/publish.ps1`, which also bumps these links.
- **Checkout** — the "Get TapeSim" buttons (`index.html`, `download.html`) link to
  the Lemon Squeezy **test-mode** buy URL. Swap for the live URL at launch.
- **Support** — `support@tapesim.app` (a dedicated Fastmail mailbox).
- **Legal** — `terms.html` / `privacy.html` / `refund.html` are filled for personal
  ownership (Marko Grdinić, Croatia); still carry a "draft — not legal advice"
  banner pending review before real payments.

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

Run a static server from this dir and open `http://localhost:8000`:

```
python3 -m http.server 8000
```

**The docs page must be served over HTTP, not opened as a `file://` URL.** `docs.html`
fetches its Markdown at runtime, and browsers block `fetch()` of local files under
`file://` (same-origin policy) — you'll get "Couldn't load this page." The plain HTML
pages open fine either way; only the docs need the server. GitHub Pages serves over
HTTPS, so this only affects local preview.
