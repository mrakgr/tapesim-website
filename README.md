# tapesim-website

Static marketing site for **TapeSim** (tapesim.app). Plain HTML/CSS — no build
step, no framework. Hosted on GitHub Pages.

## Pages

- `index.html` — landing (hero, features, how-it-works, pricing)
- `download.html` — downloads + license activation instructions
- `docs.html` + `docs/*.md` — user documentation. The HTML is a thin shell; the
  pages are Markdown rendered client-side by `marked` (CDN, SRI-pinned). `docs/_pages`
  order lives in the `PAGES` array inside `docs.html`.
- `terms.html`, `privacy.html`, `refund.html` — legal (Lemon Squeezy expects these)
- `styles.css` — shared styles (palette mirrors the desktop app)
- `CNAME` — custom domain (`tapesim.app`)
- `.nojekyll` — serve files as-is, skip Jekyll processing

## Placeholders to fill before launch

Search the HTML for `PLACEHOLDER` and the red `placeholder-tag` spans:

- **Lemon Squeezy checkout URL** — every `href="#"` on a "Get TapeSim" / "get a
  license" button (`index.html`, `download.html`).
- **Download links** — the three OS cards in `download.html` (`href="#"`); point at
  real release artifacts (e.g. GitHub Releases). Remove any OS you don't ship.
- **Screenshot** — drop an image at `assets/screenshot.png` and swap the
  `.placeholder` div in `index.html` for an `<img>`.
- **Support email** — `support@tapesim.app` throughout; set up real mail or change it.
- **Legal details** — `LEGAL ENTITY / NAME`, `ADDRESS / JURISDICTION`, dates, and
  the refund window in `terms.html` / `privacy.html` / `refund.html`. These are
  drafts — have them reviewed.

## Deploy (GitHub Pages)

1. Create a **public** repo named `tapesim-website` on GitHub.
2. Push this directory to it (`main` branch).
3. Repo **Settings → Pages**: set **Source = Deploy from a branch**, branch `main`,
   folder `/ (root)`. Save.
4. The `CNAME` file already requests `tapesim.app`. In your domain registrar /
   DNS, point `tapesim.app` at GitHub Pages:
   - apex `tapesim.app`: A records to `185.199.108.153`, `185.199.109.153`,
     `185.199.110.153`, `185.199.111.153` (GitHub Pages IPs), and/or an `ALIAS`/
     `ANAME` if your DNS supports it.
   - `www.tapesim.app`: CNAME to `mrakgr.github.io`.
5. Back in Settings → Pages, tick **Enforce HTTPS** once the cert is issued.

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
