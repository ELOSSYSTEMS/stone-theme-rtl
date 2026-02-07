/docs/01_ARCHITECTURE_CONTRACT.md
# 01_ARCHITECTURE_CONTRACT — Repo + Code Rules (Hard Contract)
Version: 0.1

## 0) Precedence
If conflict: 00_MASTER_SPEC.md > this file > others.

## 1) Directory Contract (Do Not Violate)
Allowed directories and their responsibilities:

- `layout/`  
  Global wrapper(s). Must include `{{ content_for_header }}` and `{{ content_for_layout }}`.
  Only minimal global markup here.

- `sections/`  
  Configurable modules with `{% schema %}`.
  Sections must be self-contained and robust with safe defaults.

- `blocks/`  
  Reusable components with `{% schema %}` where applicable.
  Use blocks when you need repeated component patterns across sections.

- `snippets/`  
  Small reusable fragments rendered with `{% render %}`.
  Must be pure and parameterized (no hidden global assumptions).

- `assets/`  
  Only for global/static assets.
  Rule: component-level CSS/JS should be loaded via `{% stylesheet %}` / `{% javascript %}` inside sections/blocks/snippets.
  Keep `assets/critical.css` strictly for universal essentials.

- `templates/`  
  JSON templates that compose sections.
  Templates must support presets (Theme Styles) without breaking content.

- `config/`  
  Theme settings + presets.

- `locales/`  
  Translation files for storefront strings and schema (editor) strings.

## 2) Liquid Authoring Rules
### 2.1 General
- Prefer clarity over cleverness.
- Avoid deeply nested logic. Use early returns and simple branches.

### 2.2 No Hardcoded UI Strings
- Storefront UI strings must use `{{ '...' | t }}` keys.
- Schema labels must use `t:` references and be present in schema locale JSON.

### 2.3 Safe Conditional Logic
- Liquid has limited boolean expression support; avoid complex expressions.
- Use nested `if` blocks and assign intermediate values when needed.

### 2.4 Snippet/Block Purity
- Snippets must accept parameters explicitly.
- Do not rely on implicit global variables unless Shopify guarantees them (product, collection, etc.).
- Document required parameters at the top of the snippet with a short comment.

## 3) CSS Architecture Rules
### 3.1 Bidi/RTL Rule
Use logical properties where possible:
- `margin-inline-start/end`
- `padding-inline-start/end`
- `inset-inline-start/end`
- `border-inline-start/end`
- `text-align: start/end`

Do NOT:
- Duplicate entire stylesheets for RTL.
- Hardcode `left/right` except in narrowly controlled cases with `html[dir="rtl"]` overrides.

### 3.2 Icon Mirroring Rule
Directional icons must be mirrored in RTL.
Allowed approaches:
- CSS transform on icon container in RTL contexts
- Swap SVG via CSS/inline logic
- Use a single SVG and mirror via `scaleX(-1)` in RTL

### 3.3 LTR Islands Rule
For content that must remain LTR inside RTL pages:
- Add wrapper with `dir="ltr"`
- Apply `unicode-bidi: isolate` or `unicode-bidi: plaintext` as needed
- Ensure it does not break line wrapping

Examples requiring LTR islands:
- coupon codes
- email addresses
- URLs
- SKUs
- phone numbers (often better LTR)

### 3.4 Asset Loading Rule
- Prefer component-scoped CSS/JS via `{% stylesheet %}` / `{% javascript %}`.
- `assets/critical.css` must remain minimal and universal.

### 3.5 Mobile-First Rule
CSS must be mobile-first.
Desktop enhancements only above breakpoints.

## 4) JavaScript Rules
### 4.1 Minimal JS, Progressive Enhancement
- The theme must work without JS for core navigation and product purchase when possible.
- JS can enhance sliders, drawers, predictive search.

### 4.2 No Heavy Frameworks
- No React/Vue/etc.
- No large slider libraries unless strictly justified in 04_CHANGELOG_DECISIONS.md

### 4.3 Accessibility in JS Components
- Drawers/modals must trap focus appropriately.
- Escape closes overlays.
- ARIA attributes updated correctly.

## 5) Schema Rules (Theme Editor Ergonomics)
### 5.1 Settings Hygiene
- Group settings logically (Header: Layout / Behavior / Typography / Colors).
- Avoid > 25 settings in a single section unless unavoidable.
- Provide safe defaults that produce a premium layout immediately.

### 5.2 Translation Requirements
- Every `name`, `label`, `info`, option label in schema must use `t:` references.
- Update `locales/he.schema.json` and `locales/en.default.schema.json` in the same change.

### 5.3 Presets
- Every section must have at least one preset definition.
- Presets must be designed to work across Theme Styles.

## 6) Localization Rules
### 6.1 Key Naming Convention
- Keys are snake_case, hierarchical, max ~3 levels deep.
- Example:
  - `header.menu.open`
  - `cart.empty.title`
  - `product.add_to_cart`

### 6.2 Tone Consistency
- Hebrew copy must be consistent, professional, and concise.
- Avoid slang by default (unless tone pack feature is enabled).

## 7) Engineering Checklist for Any PR/Change
Every change must include:
1) Code changes in correct directory
2) Schema label keys added/updated
3) Storefront translation keys added/updated
4) RTL/LTR smoke test notes
5) QA matrix items checked (referencing 03_QA_TEST_MATRIX.md)

## 8) “Stop Conditions” (Block Merge / Block Continue)
If any of the following happens, stop and fix before continuing:
- Any hardcoded Hebrew appears in Liquid templates (non-content)
- Drawer navigation breaks keyboard accessibility
- RTL icon direction wrong in any shipped template
- CLS visible in hero/gallery/cart drawer opening
- Missing locale keys (broken `t`)

END

