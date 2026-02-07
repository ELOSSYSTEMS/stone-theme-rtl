/docs/00_MASTER_SPEC.md
# 00_MASTER_SPEC — RTL / Hebrew-First Shopify Theme (Canonical Product Spec)
Version: 0.1  
Price Target: ₪1,250 (one-time)  
Base: Skeleton theme  
Distribution Target: Shopify Theme Store + optional private sales (same codebase)

## 0) Precedence
This file is the highest authority.
If any other doc conflicts, this wins unless an override is explicitly written here in §14 “Approved Overrides”.

## 1) Product Definition (What We Are Selling)
A Theme Store–quality Shopify theme that is:
- Hebrew-first (storefront + editor UI)
- RTL-native (true bidi correctness, not visual hacks)
- Conversion-safe for Israeli SMBs
- Fast, accessible, and maintainable
- Ships with 3 vertical presets (Theme Styles) aligned to Israel’s Shopify TAM

### 1.1 Target Customer
Israeli SMB owners (often non-technical), selling:
- Apparel / Fashion
- Home & Garden
- Beauty & Fitness

### 1.2 Buyer Promise (Marketing Claim Boundaries)
Allowed claims:
- “Hebrew-first Theme Editor labels and settings”
- “RTL-native UI with bidi-safe text handling”
- “Designed for Israeli SMB workflows (WhatsApp-ready, trust blocks, delivery messaging)”
- “Theme Store quality: performance, accessibility, and maintainability”

Forbidden claims:
- “Full RTL checkout customization”
- “Works perfectly with every app”
- “Real-time delivery ETA accuracy” (unless backed by Shopify-native data and clearly documented)

## 2) Non-Negotiables (Hard Requirements)
If any item below is not met, the theme is not shippable.

### 2.1 Hebrew-First Localization
- 100% of user-facing strings must be translatable via `t` keys.
- 100% of theme editor (schema) labels/options/presets must be translatable.
- Hebrew locale must be complete for all shipped sections/templates and flows.

### 2.2 RTL + Bidi Correctness
- RTL layout must be correct for all templates.
- LTR islands must be handled for:
  - email, URLs, SKUs, coupon codes, phone numbers, numeric-only values
- Directional UI must flip properly:
  - chevrons, arrows, carousels, breadcrumbs, pagination, back/forward logic

### 2.3 Conversion Core Must Be Strong
Must ship high-quality versions of:
- Header + mobile drawer navigation (RTL-perfect)
- Search (predictive or robust results + no-results recovery)
- Collection grid with sorting + filtering UX (mobile-first)
- Product card (badges, pricing, sold-out, optional hover image)
- PDP buy box with sticky mobile CTA option
- Cart drawer + cart page with upsell slots + trust/policy blocks
- Trust system blocks (delivery/returns/warranty/contact/WhatsApp)

### 2.4 Theme Store Quality Bar
- Accessibility baseline: keyboard navigation, focus order, aria labels, contrast-safe defaults
- Performance baseline: low CLS defaults, scoped assets, minimal global CSS
- Robust empty/error states (cart empty, no search results, missing images, sold-out)

## 3) Minimum Shipping Scope (Must Ship)
### 3.1 Templates
- Home
- Collection
- Product
- Cart
- Search
- Page
- Blog + Article (recommended; if removed, decision must be logged in 04_CHANGELOG_DECISIONS.md with rationale)

### 3.2 Sections (Minimum Set)
Global
- Header
- Footer

Home
- Hero (image + optional video)
- Featured Collection Grid
- Featured Products
- Collection List
- Editorial (image-with-text variants)
- UGC / Gallery (RTL-safe)
- Testimonials (RTL-safe)
- Brand Manifesto / Rich Text
- Trust Strip

Collection
- Collection Banner
- Collection Grid + Filter/Sort UI

Product
- Media Gallery (RTL-safe)
- Buy Box (variants + quantity + sticky CTA option)
- Product Details Accordion
- Complementary Products / Upsell
- Trust Block near CTA

Cart
- Cart Drawer
- Cart Page Summary section(s)

Utility
- FAQ
- Contact (with optional WhatsApp CTA)

### 3.3 Theme Styles (Presets)
Must ship 3 styles that feel like store-type presets (not color skins):
1) Apparel / Fashion
2) Home & Garden
3) Beauty & Fitness

Each style must define:
- Typography scale + button style + radius/shadows
- Default homepage stack (order + settings defaults)
- Product grid density defaults
- PDP emphasis defaults (gallery size, accordion usage, trust placement)

## 4) Novel Differentiators (Must Include at This Price)
At ₪1,250, the theme must include at least 4 of the following built-in differentiators:
- Smart WhatsApp Conversion Bar (template-aware)
- Trust Stack Builder (reorderable, expandable)
- Delivery Promise Block (region messaging; non-real-time)
- Gift Mode (gift note + invoice-free copy + gift wrap toggle)
- Holiday Moment Banner (date-window scheduling)

If fewer than 4 ship, price justification weakens; log a decision + adjust scope or price.

## 5) Out of Scope (Explicit)
- Checkout UI redesign beyond Shopify’s theme control
- Complex mega-app functionality (loyalty engines, subscription engines, etc.)
- Heavy client-side frameworks
- Dynamic geo-ETAs or carrier integrations unless Shopify-native and minimal

## 6) Release Milestones
- M0: Foundations complete (RTL primitives + locales scaffolding)
- M1: Global shell complete (layout + header/footer)
- M2: Shopping loop complete (collection + product card + search)
- M3: PDP + cart complete (conversion-ready)
- M4: Presets complete (3 vertical styles)
- M5: Hardening complete (QA matrix passes)
- RC: Documentation complete + version tagged

## 7) Documentation (Must Ship)
Docs folder must include:
- SETUP_HE.md (10-minute Hebrew setup)
- PRESETS_HE.md (choose preset + first changes)
- RTL_BIDI_GUIDE.md (what’s handled + edge cases)
- COMPATIBILITY.md (tested apps + known issues)
- SUPPORT_POLICY.md (scope boundaries)

## 8) Support Promise (Minimum)
- 30 days bug support (theme defects)
- Clear boundary: no free custom development
- Bug fixes released as patch versions

## 9) Quality Gates (Ship/No-Ship)
No feature is “done” unless:
- Hebrew editor labels exist (schema locale)
- Hebrew storefront strings exist (locale)
- RTL/LTR both render without breakage
- QA matrix checks for that feature pass

## 10) Decision Policy
Any scope change must be recorded in:
`/docs/04_CHANGELOG_DECISIONS.md`
including rationale and implications.

## 11) Security / Privacy
- Do not include trackers by default.
- Any analytics integration must be optional and documented.

## 12) Performance Budget (Guideline)
- Keep JS minimal; prefer progressive enhancement.
- Avoid large slider libraries unless justified.
- Ensure critical CSS stays small and universal.

## 13) Accessibility Budget (Guideline)
- Every interactive control must be reachable by keyboard.
- Visible focus states must exist in RTL and LTR.

## 14) Approved Overrides
(Empty by default. Add only when you knowingly break a rule.)
- Override ID:
- Date:
- Rule overridden:
- Reason:
- Mitigation:

## 15) Legacy Roadmap Content
(Merged from `Build Roadmap.md`; roadmap authority remains `02_BUILD_ROADMAP.md`.)

### 15.1 Operating Rules for LLM Contributions (Legacy)
When implementing any change, output should generally include:
- **Target file path(s)**
- **Complete code blocks** (not partial fragments unless explicitly requested)
- **Schema translations** updates (for editor UI) if a label/setting is introduced
- **Storefront translations** updates if user-facing text is introduced
- **QA checklist** to validate via `shopify theme dev`

Do not:
- Introduce app dependencies for core features.
- Add heavy libraries for sliders/filters unless absolutely necessary.
- Hardcode Hebrew text in Liquid; always use translation keys.
- Solve RTL by duplicating entire stylesheets; use logical properties + direction toggles.

### 15.2 Repo Structure Contract (Legacy Reference)
Work inside these directories:
- `layout/` – global wrappers
- `sections/` – configurable modules with `{% schema %}`
- `blocks/` – reusable components with `{% schema %}` (where applicable)
- `snippets/` – reusable fragments via `{% render %}`
- `assets/` – minimal, only global/critical assets
- `locales/` – translations (storefront + schema locales)
- `templates/` – JSON templates + core template assignment
- `config/` – settings schema + presets


