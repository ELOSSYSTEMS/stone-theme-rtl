# IMPLEMENTATION_PLAN — Living Plan (Single Objective Queue)
> This is the single canonical implementation plan.

Version: 0.2  
Rule: This plan is the execution queue. Keep it updated.  
Rule: One objective per IDE session/run.

## 0) Current Phase
Current Phase: PHASE_0 (Scaffold + Baseline Validation)

## 1) Next 3 Objectives (Must Stay Current)

### Objective 1 (Next) — Lock Canonical Workspace + Baseline Theme Integrity (Docs + Repo only)
- Goal: Confirm the canonical theme workspace and baseline Shopify theme integrity so subsequent work is safe and repeatable.
- Target files:
  - `/docs/IMPLEMENTATION_PLAN.md` (this file)
  - `/docs/FILE_MAP.md` (update if canonical path differs)
  - `/docs/CANONICAL_INDEX.md` (confirm all docs listed)
  - `/docs/04_CHANGELOG_DECISIONS.md` (add initial entry if not present)
  - `/docs/MIGRATION_MANIFEST.md` (ensure template exists; keep empty unless migrating)
- Dependencies:
  - `/GLOBAL_ANTIGRAVITY_RULES.md`
  - `/docs/README_FOR_IDE.md`
- Acceptance criteria references (ACCEPTANCE_CRITERIA.md):
  - Global Acceptance (no code change required in this objective)
- QA items:
  - Doc-only: N/A
  - Repo sanity: report `git status` cleanliness as PASS/FAIL/UNKNOWN (no commands executed unless user confirms)
- Decision log required? N (unless promoting a different canonical workspace path; then log “workspace promotion”)

Notes:
- If canonical theme folder path is not yet confirmed, set Target theme path lines in FILE_MAP to “TBD” and stop.

---

### Objective 2 — Create Minimum Viable Core Template Loop (Home → Collection → PDP → Cart) with RTL + i18n foundations
- Goal: Implement a stable, minimal core loop using conservative defaults that renders correctly in Hebrew RTL and does not break in English LTR.
- Target files (TBD until canonical theme path confirmed):
  - `layout/theme.liquid` (ONLY if required to ensure correct CSS/JS includes; minimize changes)
  - `templates/index.json`
  - `templates/collection.json`
  - `templates/product.json`
  - `templates/cart.json` (or cart drawer template/config if theme uses drawer pattern)
  - `sections/*` (only the minimum required sections referenced by templates)
  - `locales/he.json`, `locales/en.default.json`
  - `locales/he.schema.json`, `locales/en.default.schema.json`
  - `/docs/05_SECTION_INVENTORY.md` (register any sections added/modified)
- Dependencies:
  - `/docs/00_MASTER_SPEC.md` (minimum templates + minimum sections definition)
  - `/docs/01_ARCHITECTURE_CONTRACT.md`
  - `/docs/06_DESIGN_TOKENS.md`
  - `/docs/09_BIDI_EDGE_CASES.md`
  - `/docs/10_PERFORMANCE_PLAYBOOK.md`
  - `/docs/11_A11Y_PLAYBOOK.md`
  - `/docs/SCHEMA_SETTINGS_CONVENTIONS.md`
  - `/docs/TRANSLATION_KEYS_MAP.md`
- Acceptance criteria references (ACCEPTANCE_CRITERIA.md):
  - 2.1 Home (index)
  - 2.2 Collection
  - 2.3 Product (PDP)
  - 2.4 Cart (drawer + page) — whichever pattern is chosen
  - 1) Global Acceptance
- QA items:
  - `/docs/REGRESSION_CHECKLIST.md` (must pass)
  - `/docs/03_QA_TEST_MATRIX.md` Flow A for each template implemented (home/collection/product/cart)
  - RTL/Bidi sanity: run the 09 suite strings in header/cart/PDP surfaces
  - Performance: visually confirm no CLS in hero/gallery/cart drawer
  - A11y smoke: keyboard tab + escape close for overlays/drawers
- Decision log required? Y (template stacks + any global include changes are scope-impacting)

Notes:
- Do not introduce “nice-to-haves.” The output is “stable, minimal, eligible.”

---

### Objective 3 — Ship First Israel RTL Differentiator Section (WhatsApp / Trust / Delivery) with Conservative Defaults
- Goal: Add one high-converting Israel-specific differentiator as a Theme Store-safe section, fully localized and RTL-correct, without performance regressions.
- Recommended first differentiator (pick ONE, do not combine in this objective):
  - Option A: WhatsApp Contact Bar (non-intrusive, disable toggle)
  - Option B: Trust Strip / Trust Stack Builder (icons + short claims)
  - Option C: Delivery/Service Promise Block (strictly non-guarantee language by default)
- Target files (TBD until canonical theme path confirmed):
  - `sections/<differentiator-section>.liquid`
  - `snippets/<any-needed-icons-or-partials>.liquid` (only if required)
  - `templates/index.json` (add section to home default stack OR keep optional)
  - `locales/he.json`, `locales/en.default.json`
  - `locales/he.schema.json`, `locales/en.default.schema.json`
  - `/docs/05_SECTION_INVENTORY.md`
  - `/docs/04_CHANGELOG_DECISIONS.md`
- Dependencies:
  - `/docs/00_MASTER_SPEC.md` (must allow this differentiator in minimum shipping scope or as optional)
  - `/docs/06_DESIGN_TOKENS.md` (spacing/icon rules)
  - `/docs/07_COPY_STYLE_GUIDE_HE.md` (Hebrew wording)
  - `/docs/09_BIDI_EDGE_CASES.md`
  - `/docs/10_PERFORMANCE_PLAYBOOK.md`
  - `/docs/11_A11Y_PLAYBOOK.md`
  - `/docs/SCHEMA_SETTINGS_CONVENTIONS.md`
- Acceptance criteria references (ACCEPTANCE_CRITERIA.md):
  - 3.x component criteria relevant to differentiator (Trust / WhatsApp) + Global Acceptance
- QA items:
  - `/docs/REGRESSION_CHECKLIST.md` (must pass)
  - QA matrix items relevant to home + header/cart if affected
  - RTL/Bidi: mixed strings safe; icons direction correct
  - A11y: icon-only controls have aria-label; focus behavior stable
  - Performance: no new CLS or heavy site-wide JS
- Decision log required? Y (new shipped section + any template default inclusion)

## 2) Implementation Notes (Only What Matters)
- RTL-first: Hebrew is primary rendering target.
- i18n-first: schema + storefront keys required for any UI text.
- Do not touch high-risk files without backups if applicable (GLOBAL rules).

## 3) Open Questions (Blockers)
- Canonical theme workspace path: UNKNOWN until confirmed.
- Shopify dev theme ID and GOLDEN theme presence: UNKNOWN until confirmed.
- Cart pattern choice (drawer vs page-first): TBD based on base theme scaffold.

## 4) “Definition of Done” Reminder
A change is DONE only when:
- locale + schema i18n is complete
- RTL/bidi passes the edge suite where relevant
- no CLS introduced
- interactive elements pass keyboard/focus rules
- Section Inventory updated if any component added/changed
- Decision log updated if required

END

