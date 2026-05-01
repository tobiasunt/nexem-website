# NEXEM Website — Design Spec

**Date:** 2026-05-01
**Direction:** Brutalist-Tech / Light (Linear-style adapted for a marketing agency that also builds software)
**References:** Vercel, Resend, Stripe Press, Linear (light variant)
**Live:** https://nexem.at — repo `tobiasunt/nexem-website`, deployed via GitHub Pages on `main`

## Aesthetic Direction

Brutalist-Tech with a premium twist. Sharp angular layouts, big distinctive typography, monospaced detail labels as a visual rhythm device, asymmetric composition, dramatic type scales. Warm-light background instead of dark to feel approachable for marketing clients while keeping technical credibility.

Avoid generic AI-template aesthetics: no Inter, no purple-gradient-on-white, no centered hero with two buttons, no 3-column card grid for services.

## Typography (Google Fonts, free)

| Role | Font | Weight | Notes |
|---|---|---|---|
| Display (hero, section titles) | **Bricolage Grotesque** Variable | 600-800 | Distinctive, modern-brutalist, can run condensed |
| Body | **Geist** | 400, 500, 600 | Vercel's sans, technical feel, not Inter-derivative |
| Mono (labels, numbers) | **Geist Mono** | 400, 500 | Matched pair, signals "software" |

Mono labels in CAPS used as visual rhythm: `[ 01 / SERVICES ]`, `[ NEXT LEVEL E-COMMERCE & MARKETING ]`, `[ READY? ]`.

## Color Palette

```
--bg              #fafaf9    warm-white background
--bg-card         #ffffff    cards
--ink             #080526    primary text (NEXEM navy)
--ink-soft        #4a4960    lead / sub
--ink-mute        #8a8aa3    mono labels, meta
--accent          #0E61D1    NEXEM blue — sparing
--accent-soft     rgba(14,97,209,0.08)   hero glow, hover tints
--border          rgba(8,5,38,0.08)
--border-strong   rgba(8,5,38,0.16)
--ink-inverse     #fafaf9    on dark CTA block
--bg-dark         #080526    full-bleed CTA section
```

Subtle SVG grain texture overlay (~4% opacity) on `body::before` for depth (disabled when `prefers-reduced-motion`).

## Logo asset

`assets/logo.svg` was edited to use a tight `viewBox="105 370 790 260"` instead of the original `0 0 1000 1000`. The Adobe Illustrator export had ~75% empty padding around the wordmark — without the crop, the logo at `height: 50px` would render only ~13px of actual visible wordmark. The tight viewBox makes the rendered size match the configured CSS height. Source brand assets remain in `Logo/` (gitignored, not deployed).

## Sections (as built)

1. **Top-bar (sticky)** — height 84px desktop / 72px mobile; large logo (50px / 40px) left, nav (Leistungen · Approach · Kontakt) right with underline-on-hover.
2. **Hero (full viewport)** — asymmetric; mono eyebrow `[ NEXT LEVEL E-COMMERCE & MARKETING ]`, massive display headline "Commerce, der *performt*." (italic word in NEXEM blue), Geist subhead, primary CTA + ghost CTA with `↓` arrow. Background: radial gradient mesh in NEXEM blue (top-right), full logo as low-opacity (4.5%) watermark bottom-right rotated -4deg.
3. **Services** — 3 horizontal rows with `01`, `02`, `03` Geist Mono numbers, large titles, descriptions, capability tag pills. Hover reveals 3px blue accent border-left + slides arrow `→` in.
4. **Approach** — 4 grid cells (auto-fit minmax 220px) `→ 01 Discover`, `→ 02 Strategy`, `→ 03 Build`, `→ 04 Scale`. Each cell tints accent-soft on hover.
5. **Tech stack strip** — slim band: `Shopify · Shopware · Klaviyo · Meta Ads · Google Ads · GA4 · n8n · TypeScript`. Geist Mono separated by `•`.
6. **CTA block (full-bleed dark)** — `#080526` background with NEXEM-blue radial highlight, massive headline "Lass uns bauen.", inverse white button with `info@nexem.at →`.
7. **Contact** — single-column, left-aligned: mono `[ 03 / KONTAKT ]`, "Schreib uns." headline, huge display email link `info@nexem.at`. No address (legal info only in Impressum/Datenschutz).
8. **Footer** — minimal mono row: copyright left, Impressum + Datenschutz right.

Legal info (FN, UID, Firmenbuchgericht, full address) appears **only** in `impressum.html` and `datenschutz.html` — not on the landing page.

## Motion

- Page-load: staggered fade-up on hero elements (eyebrow → headline → subhead → CTAs), 80ms stagger, 14px translate, 720ms cubic-bezier(0.2, 0.6, 0.2, 1).
- Scroll-reveal: sections fade in at 15% intersection threshold (IntersectionObserver, no library), 18px translate, 700ms.
- Hero gradient mesh: 14s ease-in-out alternate pan loop, transform-only.
- Hover: nav-link underline scale-in, service rows accent-border-left scale-in, buttons swap background to accent.
- `prefers-reduced-motion`: all reveals snap-on; mesh pan disabled; grain disabled.

## Web Interface Guidelines compliance

- Typography: `…` not `...`, `&mdash;` for em-dashes, `&nbsp;` for brand names + `+43` numbers.
- `font-variant-numeric: tabular-nums` on all mono content.
- `text-wrap: balance` on headings, `text-wrap: pretty` on body copy.
- Images: explicit width/height attributes (no CLS); logo loads eager, watermark eager-decode-async.
- Focus-visible: 2px solid accent ring with 2px offset.
- Semantic HTML: `<a>` for navigation, `<button>` reserved for actions (only inline mailto/anchor links used currently).
- `aria-label` on logo link, `aria-hidden` on decorative icons.
- `prefers-reduced-motion` honored across all animations.
- Skip link to `#main` for keyboard users.
- `<meta theme-color>` matches background `#fafaf9`.
- `color-scheme: light` on `<html>`.
- Touch: `touch-action: manipulation` and intentional `-webkit-tap-highlight-color: transparent` on buttons.
- `translate="no"` on brand names + tech labels to prevent garbled auto-translation.

## Default copy

- Hero headline: "Commerce, der *performt*."
- Hero sub: "NEXEM verbindet strategisches Marketing mit technischer Umsetzung. Von der Kampagne bis zum Custom-Shop — aus einer Hand."
- CTA block headline: "Lass uns bauen."
- Tech stack: Shopify · Shopware · Klaviyo · Meta Ads · Google Ads · GA4 · n8n · TypeScript
- Approach steps: Discover → Strategy → Build → Scale

## Out of scope (this iteration)

- Blog / case studies (no real content yet).
- Multi-language (DE only initially).
- Analytics / cookie banner (no tracking yet — `datenschutz.html` documents this).
- Phone number (email only).
