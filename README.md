# aldyn-pages

Marketing + install-walkthrough site for **Aldyn** — local-first IRS-notice and
attorney-communication management for accountants, by Nrdyn LLC.

Plain static HTML and one stylesheet. No build step, no dependencies, no JavaScript.

## Pages

| File | URL (clean URLs are on) | Purpose |
|---|---|---|
| `index.html` | `/` | Landing page — features, screenshots, how it works, privacy |
| `install.html` | `/install` | Full macOS install walkthrough — the "instead of an App Store button" page |
| `support.html` | `/support` | FAQ and troubleshooting |
| `privacy.html` | `/privacy` | Privacy policy |

## Deploying to Vercel

Import the repo and deploy — there is no framework and no build command. Vercel
serves the directory as-is; `vercel.json` turns on clean URLs and sets the
security and cache headers.

Or from the CLI:

```bash
npx vercel        # preview
npx vercel --prod # production
```

## Before the first production deploy

The canonical URL is currently **`https://aldyn.nrdyn.com`** as a placeholder.
Once the real domain is attached in Vercel, swap it everywhere in one pass:

```bash
grep -rl 'aldyn.nrdyn.com' . --exclude-dir=.git | xargs sed -i '' 's|https://aldyn.nrdyn.com|https://YOUR-DOMAIN|g'
```

That covers the `<link rel="canonical">` tags, the Open Graph / Twitter URLs, the
JSON-LD blocks, `robots.txt` and `sitemap.xml`.

## Assets

- `assets/mark.webp` — the Aldyn crystal mark (favicons derived from it)
- `assets/og-image.png` — social card, shared with `nrdyn.com/aldyn`
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
