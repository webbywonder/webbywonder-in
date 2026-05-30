# WebbyWonder

The landing site for **WebbyWonder** — a small engineering studio in Mumbai, led by [Darshan Gada](https://darshangada.com). We build apps, AI agents and automation, and offer fractional technical leadership.

🔗 **Live:** [webbywonder.in](https://webbywonder.in)

> A single, hand-built static page. No frameworks, no backend, no build step — just `index.html`.

---

## What's here

- **`index.html`** — the entire site: markup, inline CSS, a little vanilla JS, and full SEO metadata (canonical, Open Graph, Twitter Card, JSON-LD).
- Two small runtime touches, no dependencies:
  - The years-of-experience figure auto-increments each year (career start: 2016).
  - The "requests served" number pulls a live value from the public [Country-State-City API](https://countrystatecity.in), with a baked-in fallback.
- The email address is assembled in JavaScript at runtime, so it never appears in the raw HTML (basic scraper hygiene).

---

## Project structure

```
webbywonder-in/
├── index.html      # The whole site — markup, CSS, JS, SEO meta + JSON-LD
├── favicon.svg     # WW monogram favicon (signal blue)
├── og-image.png    # Open Graph / Twitter share image (1200×630)
├── robots.txt      # Crawler directives + sitemap pointer
├── sitemap.xml     # Single-page sitemap
├── wrangler.jsonc  # Cloudflare Worker (Static Assets) deploy config
└── .assetsignore   # Files kept out of the deployed bundle (e.g. .git)
```

---

## Running locally

It's a static site, so any static server works. Serve over HTTP (not `file://`) so the live request-count fetch isn't blocked by CORS:

```bash
# Node (no install needed)
npx serve .

# or Python
python3 -m http.server 8000
```

Then open the printed URL (e.g. `http://localhost:8000`).

---

## SEO

The page ships with a complete crawlable metadata set:

- **Canonical URL** and an `index, follow` robots directive.
- **Open Graph** + **Twitter `summary_large_image`** cards backed by `og-image.png` (1200×630).
- **JSON-LD** structured data — `Organization` (WebbyWonder) + `Person` (Darshan Gada) + `WebSite`.
- **`robots.txt`** allows all crawlers and points to **`sitemap.xml`**.

---

## Deployment

Hosted on **Cloudflare Workers (Static Assets)** with the GitHub integration:

- Pushing to `main` triggers an automatic deploy via the Cloudflare ↔ GitHub build.
- `wrangler.jsonc` pins the config — serves the repo root and disables the `*.workers.dev` / preview URLs.
- `.assetsignore` keeps `.git`, local state, and docs out of the served bundle.

Domains:

- **webbywonder.in** (apex) — canonical, served by the Worker.
- **www.webbywonder.in** — 301 redirect to the apex.
- **webgeeks.in** — 301 redirect to webbywonder.in.

---

## Links

- GitHub — [github.com/dr5hn](https://github.com/dr5hn/)
- LinkedIn — [linkedin.com/in/dr5hn](https://www.linkedin.com/in/dr5hn/)
- Darshan Gada — [darshangada.com](https://darshangada.com)
- Country-State-City — [countrystatecity.in](https://countrystatecity.in)
