# Design

## Direction

**Sunrise Drenched** — full-palette commitment (ref: Mailchimp's yellow, recast as a navy-to-gold dawn). Color carries the brand across the entire scroll, not just the hero. The page is structured as a literal day cycle: pre-dawn navy at the top, warming through blue and amber, breaking into full daylight cream/gold by the middle, peaking at a bright gold CTA, and closing back into navy at the footer — night to day to night, echoing "tomorrow always rises again."

## Typography

- **Display**: Cabinet Grotesk (700/900) — geometric, confident, bold. Used for all headlines.
- **Body**: Switzer (400/500/600) — humanist grotesk, the counterweight to Cabinet Grotesk's geometry. Used for all paragraph text, labels, UI copy.
- Pairing logic: geometric + humanist contrast axis (per brand register guidance), not serif+sans and not two near-identical grotesks.
- Scale: fluid `clamp()`, ratio ≥1.25 between steps. Hero h1 ceiling 5.5rem. Letter-spacing floor -0.02em on display type.
- `text-wrap: balance` on headings, `text-wrap: pretty` on body copy.

## Color (OKLCH)

Two families: **night** (navy) for bookend sections, **dawn** (blue → amber → gold) for the warming middle, **daylight** (warm cream / sky-tinted white) for the "day has broken" sections.

```
--navy-950: oklch(0.14 0.045 256)   night bg
--navy-900: oklch(0.19 0.05 256)
--navy-800: oklch(0.27 0.06 254)    concept section bg
--blue-600: oklch(0.52 0.13 246)    how-it-works section bg
--blue-300: oklch(0.78 0.08 230)    accent label on dark
--amber-600:oklch(0.68 0.16 55)
--gold-400: oklch(0.82 0.15 82)     marquee / stats bg
--gold-300: oklch(0.88 0.12 85)     CTA bg (brightest, climax)
--cream-50: oklch(0.985 0.008 80)   "why" section bg — warm, tied to gold hue (not generic AI cream)
--skytint-50: oklch(0.965 0.012 232) testimonials bg — cool variant for rhythm
--ink-900:  oklch(0.16 0.03 256)    body text on light bg
--ink-700:  oklch(0.32 0.025 256)   secondary text on light bg
--blue-ink: oklch(0.42 0.13 246)    accent text on light bg (not the vivid bg-strength blue)
--amber-ink:oklch(0.46 0.14 55)     accent text on light bg (not the vivid bg-strength amber)
--paper-100:oklch(0.97 0.01 90)     body text on dark bg
--muted-on-dark: oklch(0.75 0.04 240)
```

Rule: background-strength saturated colors (gold-400, amber-600) are never used directly as small text color on light bg — separate "-ink" variants exist for that, keeping contrast safely ≥4.5:1.

## Section map (the day cycle)

1. Hero — navy-950, pre-dawn, horizon glow + custom SVG sun/horizon motif
2. Marquee — gold-400, navy ink (first bold color hit)
3. Concept — navy-800, phone mockup
4. How it works (4 steps) — blue-600
5. Why EarlyRise — cream-50 (day breaks)
6. Pricing — skytint-50 (cool daylight variant, for rhythm against the cream "Why" section above it), featured Premium card inverts to navy-950 for emphasis
7. CTA — gold-300 (climax, brightest moment)
8. Footer — navy-950 (night returns, cycle closes)

Note: a stats band (gold-400, between "How it works" and "Why") and a testimonials section (skytint-50, between "Why" and "Pricing") existed in earlier drafts and were removed — the app had no real usage data or reviews to back those claims. Re-add either only with real numbers/quotes.

## Motion

- One orchestrated hero load-in (CSS keyframes, not JS-gated — never hidden by default).
- Continuous ambient motion only: star twinkle, horizon glow pulse, marquee scroll.
- Interactive hover states on cards/buttons (lift + glow), ease-out-quart curves, no bounce.
- Full `prefers-reduced-motion` fallback: disables all keyframe animation.

## Components

- Phone mockup: realistic iPhone chrome (Dynamic Island, status bar, side buttons) showing the actual in-app task list UI.
- Cards used only where they're the right affordance (pricing, why) — never nested.
- Buttons: pill-shaped, gold-300/400 primary on dark sections, navy-950 primary on light sections.
