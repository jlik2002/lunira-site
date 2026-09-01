# lunira-site

Public static site for **Lunira**, served by GitHub Pages at
<https://jlik2002.github.io/lunira-site/>.

It exists for one reason: the App Store requires a reachable privacy-policy URL
at review, and the app links to both pages from its paywall and Settings.

| Page | URL |
| --- | --- |
| Landing | `/` |
| Privacy Policy | `/privacy/` |
| Terms of Use | `/terms/` |

## Why this is a separate repository

The app lives in `jlik2002/lunira-app`, which is **private** — it holds the
product spec and the internal `docs/`. Serving Pages from that repo would
publish all of it. This repo is public and contains nothing but the site.

## Editing

Plain HTML and one stylesheet, no build step. Push to `main` and Pages
redeploys in about a minute. The palette matches the app's default theme
(`src/theme/palettes.ts` in the app repo).

If the URLs here ever change, update `BRAND.termsUrl` and `BRAND.privacyUrl` in
the app's `src/brand/index.ts` to match — the app links to them directly.
