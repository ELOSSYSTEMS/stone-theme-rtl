/docs/02_BUILD_ROADMAP.md
# 02_BUILD_ROADMAP — Phased Execution Plan (LLM-Readable)
Version: 0.1  
Rule: Follow phases in order. Do not skip foundations.

## 0) How to Use This Roadmap
- Each phase has Objectives, Deliverables, Files, and Acceptance Criteria.
- A phase is “complete” only when acceptance criteria pass and QA items are checked.
- If a new feature is proposed, map it to a phase and log it in 04_CHANGELOG_DECISIONS.md.

---

## Phase 1 — Foundations (Locales + RTL primitives)
### Objectives
- Enable Hebrew-first translation workflow.
- Establish RTL/bidi core primitives.
- Prevent later rework.

### Deliverables
1) Locale files created and minimally populated:
   - `locales/en.default.json`
   - `locales/he.json`
   - `locales/en.default.schema.json`
   - `locales/he.schema.json`

2) RTL/Bidi CSS primitives:
   - Logical properties baseline
   - LTR islands utility
   - Icon mirroring convention
   - Base typography scale for Hebrew

3) `assets/critical.css` minimal foundation:
   - Root tokens: spacing, radius, typography, color hooks
   - `html[dir="rtl"]` minimal handling rules
   - Focus ring styling

### Files
- `assets/critical.css`
- `locales/*`
- (optional) `snippets/bidi-utils.liquid` if needed for reusable wrappers

### Acceptance Criteria
- Theme renders in Hebrew locale with correct `dir="rtl"` and no broken UI strings.
- LTR islands display correctly inside RTL.
- No missing translation keys for core UI placeholders.

---

## Phase 2 — Global Shell (Layout + Header + Footer)
### Objectives
- Build the persistent shell perfectly in RTL.

### Deliverables
1) `layout/theme.liquid`
- Sets `lang` and `dir`
- Includes skip-to-content
- Includes minimal critical CSS and component assets as needed

2) Header section
- Desktop nav + mobile drawer nav (RTL perfect)
- Search entry point
- Cart icon + count
- Sticky option
- Submenu navigation that feels correct in RTL

3) Footer section
- Multi-column menus
- Trust row
- Optional newsletter
- Contact links (WhatsApp optional)

### Files
- `layout/theme.liquid`
- `sections/header.liquid` (or `sections/main-header.liquid`)
- `sections/footer.liquid`
- `snippets/icon-*` as needed
- `locales/*` updates for all labels and UI strings

### Acceptance Criteria
- Drawer opens from correct side in RTL.
- All chevrons/arrows mirror in RTL.
- Keyboard navigation works across header and drawer.
- No layout jump opening drawer.

---

## Phase 3 — Shopping Loop Core (Collection + Product Card + Search)
### Objectives
- Enable browse → filter → product reliably.

### Deliverables
1) Product card component (snippet or block)
- image, title, price/compare, badges, sold out state
- optional hover image
- optional swatch/variant hint

2) Collection template + section stack
- Banner
- Filters + sort UI (mobile-first)
- Product grid with density controls

3) Search template
- Results layout
- No-results recovery (suggestions)
- Optional predictive search (if feasible without bloat)

### Files
- `snippets/product-card.liquid` (or `blocks/product-card.liquid`)
- `sections/collection-grid.liquid`
- `templates/collection.json`
- `templates/search.json`
- `sections/search-results.liquid` (if needed)
- locales updates

### Acceptance Criteria
- Filters and sorting usable on mobile RTL.
- Product cards do not break with long Hebrew titles.
- No-results state is helpful and translated.

---

## Phase 4 — PDP Conversion System
### Objectives
- Make product pages convert with minimal friction.

### Deliverables
1) Media gallery
- thumbs + carousel
- RTL-safe controls
- reserve media space to reduce CLS

2) Buy box
- variant selection (buttons/swatches as configurable)
- quantity
- sticky mobile CTA option (bottom bar)
- trust block near CTA

3) Product details accordion
- details/materials/care/delivery/returns/warranty
- fully translated labels

4) Complementary products / upsell module

### Files
- `sections/product-main.liquid` or split into blocks:
  - `blocks/product-gallery.liquid`
  - `blocks/product-buybox.liquid`
  - `blocks/product-accordion.liquid`
- `templates/product.json`
- locales updates

### Acceptance Criteria
- Variants handle unavailable states correctly.
- Sticky CTA works in RTL and does not cover content.
- Gallery does not cause visible layout shift.

---

## Phase 5 — Cart System (Drawer + Cart Page)
### Objectives
- Reduce drop-off; keep cart fast and clear.

### Deliverables
1) Cart drawer
- quantity change, remove
- upsell slot
- trust/policy snippet
- accessible (focus trap, escape close)

2) Cart page
- summary, notes optional
- upsell slot
- delivery/returns messaging block

### Files
- `sections/cart-drawer.liquid`
- `templates/cart.json`
- `sections/cart-main.liquid`
- locales updates

### Acceptance Criteria
- Keyboard accessible, focus order correct.
- LTR islands (coupon) readable.
- No flicker opening cart drawer.

---

## Phase 6 — Home Premium Blocks
### Objectives
- Make default homepage look premium instantly.

### Deliverables
- hero
- featured collections/products
- editorial
- UGC gallery
- testimonials
- manifesto
- trust strip

### Files
- `templates/index.json`
- `sections/*` as listed
- locales updates

### Acceptance Criteria
- Premium spacing and rhythm in Hebrew.
- Each section has clear, minimal settings.

---

## Phase 7 — Theme Styles (3 Vertical Presets)
### Objectives
- Make “Change theme style” = “Choose store type”.

### Deliverables
- 3 presets configured in `config/settings_data.json` (or equivalent preset mechanism)
- Preset docs: `docs/PRESETS_HE.md`
- Each preset changes more than color:
  - typography scale
  - grid density
  - homepage stack defaults
  - PDP emphasis defaults

### Acceptance Criteria
- Switching style does not erase content or break templates.
- Presets feel meaningfully distinct.

---

## Phase 8 — Novel Differentiators (Minimum 4)
### Objectives
- Ship unique Israel SMB features without apps.

### Deliverables (choose ≥4)
- Smart WhatsApp Conversion Bar
- Trust Stack Builder
- Delivery Promise (region messaging)
- Gift Mode
- Holiday Moment Banner

### Acceptance Criteria
- Fully translatable
- RTL-safe
- Doesn’t bloat performance
- Clear enable/disable settings

---

## Phase 9 — Hardening (A11y + Perf + QA)
### Objectives
- Reach Theme Store quality.

### Deliverables
- QA matrix passes
- Documentation complete
- Version tag and changelog entry

### Acceptance Criteria
- No critical regressions across RTL/LTR
- Accessibility baseline proven
- Performance stable (no obvious red flags)

---

## Next 3 Tasks (KEEP UPDATED)
1) Create locale files (he/en) + key naming conventions.
2) Implement bidi primitives + LTR island utilities in `assets/critical.css`.
3) Implement `layout/theme.liquid` with `lang/dir`, skip link, and minimal head.

END

