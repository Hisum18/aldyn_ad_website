# aldyn-pages

Marketing + install-walkthrough site for **Aldyn** — local-first IRS-notice and
attorney-communication management for accountants, by Nrdyn LLC.

Plain static HTML and one stylesheet. No build step, no dependencies, no JavaScript.

Live at **https://aldyn.nrdyn.com**.

## Pages

| File | URL (clean URLs are on) | Purpose |
|---|---|---|
| `index.html` | `/` | Landing page — features, screenshots, how it works, privacy |
| `install.html` | `/install` | Full macOS install walkthrough — the "instead of an App Store button" page |
| `support.html` | `/support` | FAQ and troubleshooting |
| `privacy.html` | `/privacy` | Privacy policy |

## Deploying (Netlify)

The site is deployed on Netlify from this repo (`aldyn-nrdyn/aldyn_website`):
there is no framework and no build command, the publish directory is the repo
root, and `netlify.toml` turns on the security and cache headers. Netlify's
asset server resolves the clean URLs (`/install` → `install.html`) natively.
Pushing to `main` deploys.

`vercel.json` is kept so the site can also be deployed as-is to Vercel, with
the same clean URLs and headers.

DNS: `aldyn.nrdyn.com` is a CNAME to the site's `*.netlify.app` hostname,
managed at Namecheap.

## The canonical URL

Every canonical tag, Open Graph / Twitter URL, JSON-LD block, `robots.txt` and
`sitemap.xml` entry uses **`https://aldyn.nrdyn.com`**, the live domain. If it
ever changes, swap it everywhere in one pass:

```bash
grep -rl 'aldyn.nrdyn.com' . --exclude-dir=.git | xargs sed -i '' 's|https://aldyn.nrdyn.com|https://NEW-DOMAIN|g'
```

## Assets

- `assets/mark.webp` — the Aldyn crystal mark (favicons derived from it)
- `assets/og-image.png` — social card, shared with `nrdyn.com/products`
- `assets/shots/` — product screenshots (WebP)

Screenshots are referenced with explicit `width`/`height` so the page doesn't
shift as they load. If you replace one, update those attributes to match.

## Notes on the copy

The install walkthrough tracks `aldyn/INSTALL.md` (the deployment MOP). If the
installer procedure, prerequisites or troubleshooting table change there, update
`install.html` to match.

The privacy page is deliberately explicit that AI features pass case content to
Claude Desktop, and therefore to Anthropic, under the user's own subscription —
please keep that accurate if the AI architecture changes.

© 2026 Nrdyn LLC.
