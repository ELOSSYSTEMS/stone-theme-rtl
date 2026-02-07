> [!WARNING]
> Deprecated; merged into 00_MASTER_SPEC; roadmap authority is 02_BUILD_ROADMAP.

# RTL / Hebrew-First Shopify Theme — Build Roadmap (LLM Execution Plan)
Version: v0.1  
Target Price: ₪1,250  
Base: Skeleton theme (Theme Store eligible starting point)  
Goal: Ship a marketable, conversion-safe, Hebrew-first RTL theme with 3 vertical presets and Theme Store-level quality.

---

## 0) Non-Negotiable Product Promise
This theme must deliver:
1) Hebrew-first storefront + Hebrew-first Theme Editor labels/settings (schema locales).
2) RTL-native UI with correct bidi behavior (RTL layout + LTR islands).
3) Conversion-ready commerce core (header/nav, search, collection filters, PDP buy box, cart drawer).
4) 3 “Theme Styles” that feel like category presets (not just color skins): Apparel, Home & Garden, Beauty & Fitness.
5) Performance + accessibility baseline at Theme Store standard.

If a feature creates instability, slowdowns, or editor confusion, it is out unless essential.

---

## 1) Operating Rules for LLM Contributions
When implementing any change, output must include:
- **Target file path(s)**
- **Complete code blocks** (not partial fragments unless explicitly requested)
- **Schema translations** updates (for editor UI) if a label/setting is introduced
- **Storefront translations** updates if user-facing text is introduced
- **QA checklist** to validate via `shopify theme dev`

Do not:
- Introduce app dependencies for core features.
- Add heavy libraries for sliders/filters unless absolutely necessary (prefer minimal JS).
- Hardcode Hebrew text in Liquid; always use translation keys.
- Solve RTL by duplicating entire stylesheets; use logical properties + direction toggles.

---

## 2) Repo Structure Contract (Do not violate)
Work inside these directories:
- `layout/` – global wrappers
- `sections/` – configurable modules with `{% schema %}`
- `blocks/` – reusable components with `{% schema %}` (where applicable)
- `snippets/` – reusable fragments via `{% render %}`
- `assets/` – minimal, only global/critical assets
- `locales/` – translations (storefront + schema locales)
- `templates/` – JSON templates + core template assignment
- `config/` – settings schema + presets
- `blocks/` – reusable block primitives

---

## 3) Deliverables Inventory (Minimum Shipping Set)

### 3.1 Templates (must ship)
- Home
- Collection
- Product
- Cart
- Search
- Page
- Blog + Article (recommended at ₪1,250; if skipped, document rationale)

### 3.2 Core Sections (must ship)
**Global**
- Header (RTL menu + drawer + sticky option + search + cart)
- Footer (multi-column + trust row + newsletter optional)

**Home**
- Hero (image + optional video)
- Featured Collection Grid
- Featured Products
- Collection List
- UGC / Gallery (RTL-safe)
- Testimonials (RTL-safe)
- Brand Manifesto / Rich Text
- Trust Strip (icons + text)

**Collection**
- Collection Banner
- Collection Grid + Filters + Sort

**Product**
- Media Gallery (RTL-safe)
- Buy Box (variants + quantity + sticky CTA on mobile)
- Product Details Accordion (materials/care/shipping/returns/warranty)
- Complementary Products / Upsell
- Trust Block near CTA

**Cart**
- Cart Drawer
- Cart Page Summary + Upsell slot + Trust/Policy block

**Utility**
- FAQ section
- Contact section (optional WhatsApp CTA)

### 3.3 Theme Styles / Presets (must ship)
- Apparel / Fashion
- Home & Garden
- Beauty & Fitness

Each style must define:
- Typography scale + button style + radius
- Section defaults on Home template
- Product card density + collection grid density
- PDP emphasis choices (gallery sizing, accordions, trust placement)

---

## 4) Phased Build Plan (LLM-Executable)

## Phase 1 — Foundations (RTL + Locale Infrastructure)
### Objectives
- Establish the bidi and typography foundation before building UI components.
- Ensure every future section can be translated and is RTL/LTR safe.

### Tasks
1) **Direction & bidi primitives**
   - Add global direction handling: ensure `dir` is set correctly from locale.
   - Create CSS helpers:
     - LTR-islands utility: `[dir="ltr"]` + `unicode-bidi` isolation strategy.
     - Icon mirroring strategy for chevrons/arrows in RTL.
   - Use logical properties (`margin-inline-*`, `padding-inline-*`, `inset-inline-*`).

2) **Typography system (Hebrew-first)**
   - Define 2–3 font slots (heading/body/accent optional).
   - Set Hebrew-friendly defaults (line-height, font-weight mapping).
   - Ensure numbers don’t break Hebrew lines.

3) **Locales: storefront + schema**
   Create:
   - `locales/en.default.json`
   - `locales/he.json`
   - `locales/en.default.schema.json`
   - `locales/he.schema.json`

   Populate with:
   - Core UI strings: cart, search, filters, sorting, error states, accessibility labels.
   - Schema labels for the first batch of sections (Header/Footer/Hero/etc.).

### Acceptance Criteria
- A page renders correctly in RTL with mixed content (Hebrew + numbers + URL).
- No hardcoded Hebrew strings in Liquid.
- Theme Editor displays Hebrew labels for built sections when locale is Hebrew.

---

## Phase 2 — Global Shell (Layout + Header/Footer)
### Objectives
- Build the “always visible” elements with perfect RTL behavior.

### Tasks
1) `layout/theme.liquid`
   - Ensure correct structure: head/meta, content injection, skip-to-content link.
   - Add `dir` and `lang` attributes reliably.
   - Include critical CSS minimal.

2) Header Section
   - Features:
     - RTL menu + nested menu support
     - Drawer navigation (mobile)
     - Search icon/entry point
     - Cart icon with count
     - Sticky option
   - Requirements:
     - Large tap targets
     - No flicker on drawer open/close
     - Back navigation in RTL feels native

3) Footer Section
   - Multi-column menus
   - Trust row (delivery/returns/warranty/contact)
   - Optional newsletter block
   - RTL-safe alignment and spacing

### Acceptance Criteria
- Drawer opens from correct side in RTL.
- Chevrons, back arrows, and submenu transitions are direction-correct.
- Header and footer spacing feels premium in Hebrew.

---

## Phase 3 — Commerce Core (Collection + Product Card + Search)
### Objectives
- Build “shopping loops”: browse → filter → product → cart.

### Tasks
1) Product Card (block or snippet)
   - Must include:
     - Primary image + optional secondary hover image
     - Badges (sale, sold out, custom tag badge)
     - Price + compare-at
     - Variant indicators (optional)
   - RTL-safe alignment and text overflow handling.

2) Collection Grid Section
   - Grid density settings
   - Responsive breakpoints
   - Sorting control (theme-level)
   - Filters:
     - Start minimal: product type, vendor, price, availability, tags (where applicable)
     - Must be RTL-safe UI
     - Avoid heavy JS; progressive enhancement if possible

3) Search
   - Predictive search (if implemented) or fast search results template
   - No-results recovery state:
     - Suggested collections
     - Popular products block
   - RTL highlighting

### Acceptance Criteria
- Collection filtering is usable on mobile in RTL.
- Product cards don’t break in Hebrew (long words, mixed numerals).
- Search no-results state is not a dead end.

---

## Phase 4 — PDP System (Gallery + Buy Box + Trust)
### Objectives
- Make PDP convert with minimal friction for Israeli buyers.

### Tasks
1) Media Gallery
   - Carousel + thumbnails
   - RTL-safe swipe + arrow controls
   - Good CLS behavior (reserve space)

2) Buy Box
   - Variant selection UX (buttons/swatches where possible)
   - Quantity
   - Sticky mobile CTA option (bottom bar)
   - “Trust near money” block under CTA

3) Product Details Accordion
   - Content tabs: Details, Materials, Care, Delivery & Returns, Warranty
   - Fully translated labels
   - RTL-safe toggles and icons

4) Upsell / Complementary Products
   - Optional section below buy box or below details

### Acceptance Criteria
- Variant UX doesn’t create “broken state” when unavailable.
- Sticky CTA does not cover content and respects RTL.
- Trust block appears near CTA and is editable in theme editor.

---

## Phase 5 — Cart System (Drawer + Page + Upsells)
### Objectives
- Reduce drop-off; keep cart fast.

### Tasks
1) Cart Drawer
   - Edit quantity, remove items
   - Notes optional
   - Upsell slot (manual or collection-based)
   - Trust/policy snippet

2) Cart Page
   - Clear summary
   - Upsell slot
   - Shipping/returns messaging controls
   - RTL-safe layout and focus order

### Acceptance Criteria
- Cart drawer fully keyboard navigable.
- No layout shift when opening drawer.
- Mixed LTR content (discount codes, URLs) remains readable.

---

## Phase 6 — Home Page Blocks (Premium + Vertical-ready)
### Objectives
- Provide a home experience that looks premium immediately with defaults.

### Tasks
- Hero (image/video)
- Featured collections
- Featured products
- Editorial image-with-text
- UGC gallery
- Testimonials
- Manifesto
- Trust strip

### Acceptance Criteria
- Default home preset looks premium with placeholder content.
- RTL spacing and typography read as “quiet luxury,” not cramped.

---

## Phase 7 — Theme Styles (3 Vertical Presets)
### Objectives
- Make “Change theme style” feel like “choose your store type”.

### Implementation Rules
Each preset must change:
- Typography scale and button styling
- Grid density + spacing rhythm
- Default home section stack
- Product card emphasis
- PDP emphasis (gallery/buy box balance)
Not allowed:
- Presets that only change colors.

### Preset Definitions (minimum)
1) **Apparel / Fashion**
   - Editorial hero
   - Larger imagery, variant emphasis, quick add optional
2) **Home & Garden**
   - Whitespace, room-based storytelling, larger product tiles
3) **Beauty & Fitness**
   - Benefits-first PDP layout, bundles/upsells emphasized, reviews/testimonials prominent

### Acceptance Criteria
- Switching styles does not destroy merchant content.
- Presets produce coherent store without requiring metafields.

---

## Phase 8 — Accessibility + Performance Hardening (Theme Store Quality)
### Objectives
- Pass reviewer expectations.

### Tasks
- Keyboard navigation for menus/drawers/modals
- Focus rings and aria labels
- Contrast checks for defaults
- Reduce CLS (reserve media space)
- Ensure critical CSS minimal; component assets scoped
- Remove unused JS/CSS

### Acceptance Criteria
- Lighthouse (directional target): no obvious red flags for performance/accessibility.
- Mobile Safari RTL works (key for Israel).

---

## 5) RTL/Bidi QA Matrix (LLM Must Use)
Test these flows in Hebrew locale:
1) Home → Collection → Filter → Product → Add to cart → Cart drawer → Checkout
2) Search → No results → recovery click → product
3) Menu open/close, submenu navigation, back navigation
4) Long Hebrew titles + numerals + English words
5) Discount code entry (LTR) inside RTL layout
6) Email/URL display in footer and contact blocks

Pass criteria:
- No mirrored icons wrong direction
- No unreadable mixed strings
- No layout collapse on mobile

---

## 6) Documentation Deliverables (required at ₪1,250)
Create `/docs/`:
- `/docs/SETUP_HE.md` — 10-minute Hebrew setup guide
- `/docs/PRESETS_HE.md` — which preset fits which store + what to change first
- `/docs/RTL_BIDI_GUIDE.md` — known pitfalls and how theme handles them
- `/docs/COMPATIBILITY.md` — tested apps + known conflicts + disclaimers
- `/docs/SUPPORT_POLICY.md` — 30-day support scope; bug vs customization boundary

---

## 7) Execution Order (Immediate Next Steps)
### Next 3 tasks to start now
1) Phase 1 locales + schema locales scaffolding (he/en) and translation key conventions.
2) Add bidi CSS primitives + LTR island utilities + icon mirroring standard.
3) Implement `layout/theme.liquid` with correct `dir/lang` + minimal critical CSS pipeline.

---

## 8) Definition of Done (Release Candidate)
A release candidate exists only if:
- Hebrew storefront strings are complete for core commerce flows.
- Theme Editor labels/settings are translated for all shipped sections.
- RTL + LTR both work (LTR is secondary but must not break).
- 3 presets are truly vertical-ready and stable.
- Cart, PDP, collection, search pass the QA matrix.
- Docs exist and match actual behavior.

END

