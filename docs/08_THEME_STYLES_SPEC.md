/docs/08_THEME_STYLES_SPEC.md
# 08_THEME_STYLES_SPEC — Vertical Presets (Theme Styles) Spec
Version: 0.1  
Goal: Make “Change theme style” feel like “Choose your store type.”

## 0) Rules
- Styles must change structure + defaults, not only colors.
- Styles must not delete merchant content.
- Styles must not require metafields to look correct.
- Each style must have: Home stack, Collection defaults, PDP defaults, Cart defaults.

## 1) Shared Baseline (All Styles)
- Same core sections and templates.
- Same RTL primitives and i18n completeness.
- Same trust system available.

## 2) Style A — Apparel / Fashion
**Intent:** Editorial, image-led, variant-first.

### Home Defaults
- Hero: large, editorial layout, single primary CTA
- Featured collections: prominent category navigation
- Featured products: 2–3 rows, larger cards
- Editorial: enabled by default (story block)
- UGC/testimonials: mid-page to build trust

### Collection Defaults
- Grid density: medium
- Card emphasis: image first, minimal secondary text
- Quick add: optional (off by default; can be enabled)

### PDP Defaults
- Gallery prominence: high
- Buy box: sticky CTA enabled on mobile
- Size guide block: enabled (template-level)
- “Before you buy” checklist: enabled (optional section)

### Cart Defaults
- Upsell slot: enabled (manual collection)
- Trust block: visible near totals

## 3) Style B — Home & Garden
**Intent:** Architectural whitespace, calm, larger spacing.

### Home Defaults
- Hero: calm, whitespace, softer overlay
- Featured collections: room/category based
- Editorial blocks: 2 stacked editorial sections
- Featured products: fewer products, larger tiles
- Manifesto: enabled
- Trust strip: near top (subtle)

### Collection Defaults
- Grid density: low-medium (larger tiles)
- Filters: visible but non-aggressive

### PDP Defaults
- Details accordion: expanded emphasis on materials/care
- Gallery: medium prominence, stable aspect ratio
- Trust near CTA: enabled

### Cart Defaults
- Minimal upsell (1 slot)
- Delivery promise block visible

## 4) Style C — Beauty & Fitness
**Intent:** Benefit-first, proof-heavy, bundle-ready.

### Home Defaults
- Hero: benefit headline + CTA
- Testimonials: early (above fold or near)
- UGC: enabled
- Featured products: more products, tighter grid
- Trust strip: near top

### Collection Defaults
- Grid density: medium-high
- Badges: benefit badges enabled (manual labels)

### PDP Defaults
- Buy box: high prominence
- Proof rail: enabled near CTA
- Accordion: includes “שימוש” / “מרכיבים” / “אחריות”
- Upsell/bundles: enabled (theme-native slot)

### Cart Defaults
- Upsell slot enabled
- Installments messaging block enabled (manual)

## 5) Implementation Checklist
For each style define:
- Typography scale settings (heading size, body size)
- Button style (radius, border)
- Grid gaps and density
- Default section order in `templates/index.json`
- Default section settings data (safe)
- Ensure Hebrew strings present for style-specific content

## 6) QA for Styles
- Switch style: confirm content remains; only settings/layout change
- Run Flow A and B in Hebrew locale for each style
- Confirm no style introduces CLS

END

