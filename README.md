# lunira-site

Public site for **Lunira**, served by GitHub Pages at
<https://jlik2002.github.io/lunira-site/>.

Two jobs: a landing page, and the legal pages the App Store requires at review.
The app links to the latter directly from its paywall and Settings.

| Page | URL |
| --- | --- |
| Landing | `/` |
| Privacy Policy | `/privacy/` |
| Terms of Use | `/terms/` |

## Why this is a separate repository

The app lives in `jlik2002/lunira-app`, which is **private** — it holds the
product spec and the internal `docs/`. Serving Pages from that repo would
publish all of it. This repo is public and contains nothing but the site.

## Before launch — two things to swap

1. **The App Store link.** `index.html` has one `<a class="cta">` pointing at
   `https://www.apple.com/app-store/` as a placeholder, marked with a comment.
   Point it at the real product URL.
2. **The button itself.** Once the app is listed, Apple's marketing guidelines
   require its official "Download on the App Store" badge rather than a custom
   button. Swap the `<a class="cta">` for the badge asset then — not before,
   since using it for an unlisted app is what the guidelines prohibit.

## How it is built

Plain HTML and one stylesheet. No build step, no dependencies. Push to `main`
and Pages redeploys in about a minute.

**Type.** Three faces, each with one job, so the typography says what a thing
is: `Fraunces` is the app speaking (statements, headings), `Karla` is prose,
and `DM Mono` is money — every figure, everywhere, including the `$90` in the
headline.

**Colour** comes from the app's own default theme (`src/theme/palettes.ts` in
the app repo): blush ground, deep-rose accent, plum-black ink. Light only, on
purpose — the app is light-only too, and a dark blush reads as mud.

**Images** in `img/` are real artefacts, not mockups: the mascot from
`assets/mascot/`, and four component renders from `content/cards/`, which the
app generates from its actual components with sample money.

**Motion** follows the same rule the product does: it doesn't raise its voice.
Long durations, soft easing, no bounce, no overshoot, and nothing that pulses
for attention — the CTA deliberately stays still, because an app about not
nagging shouldn't nag. The hero plays a load sequence in which the quiet second
line arrives late, as an answer. The mascot breathes on a 7-second cycle.
Everything below the fold reveals on scroll.

The hero animates from CSS alone so it survives with JavaScript off; scroll
reveals need the script, and a `<noscript>` block un-hides them when there
isn't one. `prefers-reduced-motion` disables all of it.

**The two risks on the page**, both deliberate:

1. The "same $90, said two ways" section. The left-hand panel is *meant* to be
   ugly — cold grey, alarm red, shouting caps. The contrast with the right-hand
   panel is the product argument; soften it and the section stops working.
2. Those two panels animate with opposite easings. The loud one snaps in hard
   with an overshoot; the calm one settles slowly, 0.45s later, with none. It
   is the only place on the site where motion is allowed to be abrupt, and
   that's the point — matching them would flatten the argument.
