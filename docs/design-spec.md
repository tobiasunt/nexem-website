# NEXEM Website — Design Spec

**Date:** 2026-05-01
**Direction:** Brutalist-Tech / Light (variant of Linear-style adapted for a marketing agency that also builds software)
**References:** Vercel, Resend, Stripe Press, Linear (light variant)

## Aesthetic Direction

Brutalist-Tech with a premium twist. Sharp angular layouts, big distinctive typography, monospaced detail labels as a visual rhythm device, asymmetric composition, dramatic type scales. Warm-light background instead of dark to feel approachable for marketing clients while keeping technical credibility.

Avoid generic AI-template aesthetics: no Inter, no purple-gradient-on-white, no centered hero with two buttons, no 3-column card grid for services.

## Typography (Google Fonts, free)

| Role | Font | Weight | Notes |
|---|---|---|---|
| Display (hero, section titles) | **Bricolage Grotesque** Variable | 600-800 | Distinctive, modern-brutalist, can run condensed |
| Body | **Geist** | 400, 500, 600 | Vercel's sans, technical feel, not Inter-derivative |
| Mono (labels, numbers) | **Geist Mono** | 400, 500 | Matched pair, signals "software" |

Mono labels in CAPS used as visual rhythm: `[01 / SERVICES]`, `INFO@NEXEM.AT`, `EST. 2024`, `DORNBIRN, AT`.

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
```

Subtle SVG grain texture overlay (~3% opacity) for depth.

## Sections

1. **Top-bar (sticky)** — slim, mono `[NEXEM • DORNBIRN, AT]` left, nav right with underline-on-hover.
2. **Hero (full viewport)** — asymmetric:
   - Mono eyebrow: `[NEXT LEVEL E-COMMERCE & MARKETING]`
   - Massive display headline (clamp 60-120px), accent word in NEXEM blue
   - 2-line subhead in Geist, max 60ch
   - Primary CTA + secondary text-link with arrow
   - Background: radial gradient mesh in NEXEM blue (top-right), grain overlay
   - Logo "X" cut as huge low-opacity background element bottom-right
   - Mono detail strip: `EST. 2024 • DORNBIRN, AT • ATU79849336`
3. **Services** — 3 horizontal rows with mono numbers (60px Geist Mono `01`, `02`, `03`), large titles, descriptions, optional sub-capability list. Hover: 4px blue accent border-left animates in.
4. **Approach** — 4 horizontal steps `→ 01 Discover`, `→ 02 Strategy`, `→ 03 Build`, `→ 04 Scale`.
5. **Tech stack strip** — slim band: `Shopify · Shopware · Klaviyo · Meta Ads · Google Ads · GA4 · n8n · TypeScript`. Mono labels separated by `•`.
6. **CTA block (full-bleed dark)** — navy #080526 background, massive light headline "Lass uns bauen.", inverted button. Visual hard-cut from light page.
7. **Contact** — two-column: left `[ KONTAKT ]` mono + email + opening hours; right address + Google Maps link.
8. **Footer** — minimal, mono labels, copyright, Impressum, Datenschutz.

## Motion

- Page-load: staggered fade-up on hero elements (eyebrow → headline → subhead → CTAs), 80ms stagger, 16px translate, 400ms ease-out.
- Scroll-reveal: sections fade in at 30% intersection (IntersectionObserver, no library).
- Hero gradient mesh: subtle 8s pan loop, transform-only.
- Hover: link underline on, service rows accent-border-left, buttons scale(1.02) + soft shadow.
- `prefers-reduced-motion`: all transitions reduced to 0.01ms; no panning gradient.

## Web Interface Guidelines compliance (built in from day one)

- Typography: `…` not `...`, curly quotes `"` `"`, `&nbsp;` for "+43&nbsp;…", brand names, `nexem.at`.
- `font-variant-numeric: tabular-nums` on all mono numbers.
- `text-wrap: balance` on all headings.
- Images: explicit width/height; below-fold `loading="lazy"`.
- Focus-visible: 2px solid accent ring with 2px offset.
- Semantic HTML: `<button>` for actions, `<a>` for navigation.
- `aria-label` on icon-only controls.
- `prefers-reduced-motion` honored.
- Skip link for keyboard users.
- `<meta theme-color>` matches background.
- `color-scheme: light` on `<html>`.
- Touch: `touch-action: manipulation` on interactive elements.

## Default copy answers

- Tech stack: Shopify · Shopware · Klaviyo · Meta Ads · Google Ads · GA4 · n8n · TypeScript
- Approach steps: Discover → Strategy → Build → Scale
- Phone: omitted (email only); openable later.

## Out of scope

- Blog / case studies (no real content yet).
- Multi-language (DE only initially).
- Analytics / cookie banner (no tracking yet — datenschutz.html documents this).
