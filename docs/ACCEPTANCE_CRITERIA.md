/docs/ACCEPTANCE_CRITERIA.md
# ACCEPTANCE_CRITERIA — What “Done” Means (Objective, Testable)
Version: 0.1  
Rule: No component is “shipped” unless its criteria is met.

## 1) Global Acceptance (Applies Everywhere)
- Hebrew RTL renders correctly with no broken alignment.
- English LTR does not break layout.
- No missing translations (storefront + schema).
- No fatal JS errors in console on core pages.
- No “section not found” errors in theme editor.
- Focus visible and keyboard usable for interactive controls.

## 2) Core Templates
### 2.1 Home (index)
Done when:
- Hero loads without CLS.
- Featured collections/products render correctly in RTL.
- At least one trust element present (trust strip or trust stack).
- Mobile spacing matches token rhythm.
- QA Flow A passes.

### 2.2 Collection
Done when:
- Grid loads fast, stable, no CLS.
- Sort control works.
- Filters (if enabled) work and are RTL-correct (drawer side, labels).
- Product cards show price, badges, and are bidi-safe.
- QA Flow A passes for collection.

### 2.3 Product (PDP)
Done when:
- Gallery reserves space; no CLS when images load.
- Variant selection is functional and accessible.
- Add-to-cart works (drawer + page cart).
- Sticky CTA (if enabled) is RTL-correct and does not block essential UI.
- Accordion content is readable and accessible.
- QA Flow A + key RTL edge cases pass.

### 2.4 Cart (drawer + page)
Done when:
- Quantity changes work.
- Remove item works.
- Checkout CTA visible.
- Drawer traps focus and closes with Escape.
- Coupon input (if present) is `dir="ltr"` and readable.
- QA Flow A passes.

## 3) Components
### 3.1 Header / Nav
Done when:
- Drawer opens/closes; returns focus to trigger.
- Menu hierarchy is navigable and RTL-aligned.
- Search entry accessible; icon-only controls have aria-labels.
- Bidi: phone/email in header render correctly.

### 3.2 Product Card
Done when:
- Title/price/badges align in RTL.
- Compare-at price renders correctly.
- Any SKU-like or Latin fragments do not reorder incorrectly.

### 3.3 Trust Strip / Trust Stack
Done when:
- Icons align, text concise.
- No exaggerated claims by default.
- Works in all templates where enabled.

### 3.4 WhatsApp Bar (if shipped)
Done when:
- Non-intrusive on mobile.
- Opens link correctly.
- Has disable toggle and no performance regression.

## 4) Theme Styles Presets
Done when:
- Each preset changes structure + defaults (not only color).
- Switching styles does not delete content.
- Home stack defaults match 08_THEME_STYLES_SPEC.
- QA Flow A passes in Hebrew for each preset.

END

