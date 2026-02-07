/docs/README_FOR_IDE.md
# README_FOR_IDE — How the LLM Must Operate in This Repo
Version: 0.3  
Audience: IDE agents (ChatGPT / Antigravity) contributing code and docs.  
Prime Directive: Do not improvise. Follow the canon. Log decisions.

---

## 0) Prime Directive
Operate as a deterministic builder:
- Follow the canonical documents in precedence order.
- Do not invent scope, copy, settings, or architecture.
- When required inputs are missing, stop and request them.
- Any scope-impacting change requires a decision log entry.

---

## 1) Mandatory Startup Set (Must Open First)
Before any code work, open/read:
1) `/GLOBAL_ANTIGRAVITY_RULES.md`
2) `/docs/CANONICAL_INDEX.md`
3) `/docs/FILE_MAP.md`
4) `/docs/IMPLEMENTATION_PLAN.md`

Rule:
- Update `/docs/IMPLEMENTATION_PLAN.md` “Next 3 Objectives” at the start of each session.

---

## 2) Canonical Documents (Precedence: Highest → Lowest)
If any conflict exists, the higher document wins.

### Tier A — Product + Rules (Hard Authority)
1) `/docs/00_MASTER_SPEC.md`  
2) `/docs/01_ARCHITECTURE_CONTRACT.md`  
3) `/docs/06_DESIGN_TOKENS.md`  
4) `/docs/07_COPY_STYLE_GUIDE_HE.md`  
5) `/docs/09_BIDI_EDGE_CASES.md`  
6) `/docs/10_PERFORMANCE_PLAYBOOK.md`  
7) `/docs/11_A11Y_PLAYBOOK.md`  

### Tier B — Execution + Validation (Enforcement)
8) `/docs/02_BUILD_ROADMAP.md`  
9) `/docs/03_QA_TEST_MATRIX.md`  
10) `/docs/05_SECTION_INVENTORY.md`  
11) `/docs/08_THEME_STYLES_SPEC.md`  
12) `/docs/04_CHANGELOG_DECISIONS.md`  

### Tier C — Customer-Facing Governance (Truthfulness)
13) `/docs/SUPPORT_POLICY.md`  
14) `/docs/COMPATIBILITY.md`  

---

## 3) Operational Docs (Mandatory, Non-Precedence)
These do not override Tier A/B/C, but they are REQUIRED for fast, correct execution:
- `/docs/CANONICAL_INDEX.md` (map of governance)
- `/docs/FILE_MAP.md` (where to edit)
- `/docs/IMPLEMENTATION_PLAN.md` (execution queue)
- `/docs/ACCEPTANCE_CRITERIA.md` (what “done” means)
- `/docs/TRANSLATION_KEYS_MAP.md` (i18n namespace governance)
- `/docs/SCHEMA_SETTINGS_CONVENTIONS.md` (editor UX conventions)
- `/docs/ERROR_BUDGET.md` (complexity/perf limits)
- `/docs/REGRESSION_CHECKLIST.md` (default quick QA)
- `/docs/KNOWN_PITFALLS.md` (gotchas)
- `/docs/RELEASE_CHECKLIST.md` (RC readiness)
- `/docs/ANTIGRAVITY_WORKFLOWS.md` (runbooks)

Rule:
- Before adding a new section: consult `FILE_MAP`, `SCHEMA_SETTINGS_CONVENTIONS`, and `SECTION_INVENTORY`.

---

## 4) Required Output Format for Any Implementation Task
For any requested change, output must include:

### 4.1 Scope Header (one screen max)
- Goal (single sentence)
- Files to change (explicit paths)
- Assumptions (only if unavoidable; otherwise request missing inputs)
- QA checks to run (reference 03_QA_TEST_MATRIX items + REGRESSION_CHECKLIST)

### 4.2 Code Delivery Standard
- Prefer complete files when feasible.
- If editing existing files, provide:
  - explicit anchors for replacement, OR
  - full updated file content.
- Do not output partial snippets that cannot be pasted.

### 4.3 Localization Checklist (Mandatory)
If any user-facing string or schema label is introduced/changed:
- Update:
  - `locales/he.json`
  - `locales/en.default.json`
  - `locales/he.schema.json`
  - `locales/en.default.schema.json`
- Confirm: no hardcoded Hebrew UI strings in Liquid/JSON schema.

### 4.4 RTL/Bidi Checklist (Mandatory)
Confirm:
- Logical CSS used where possible; no left/right hacks without RTL guard.
- Directional icons mirror in RTL (per Design Tokens + Bidi Playbook).
- LTR islands applied for email/URL/SKU/coupon/phone/numbers where required.

### 4.5 Performance Checklist (Mandatory)
Confirm:
- No site-wide JS introduced unless justified and logged.
- CLS prevented (hero/gallery/cart drawer).
- Component assets are scoped.

### 4.6 Accessibility Checklist (Mandatory)
Confirm:
- Keyboard navigation works.
- Focus visible and managed (drawers/modals).
- ARIA labels for icon-only buttons.

### 4.7 Inventory + Presets Checklist (Mandatory)
If you add or modify:
- Any section/snippet/block → update `05_SECTION_INVENTORY.md`.
- Any Theme Style defaults → update `08_THEME_STYLES_SPEC.md` and log in `04_CHANGELOG_DECISIONS.md`.

---

## 5) When to Stop and Ask Instead of Guessing
Stop and request input if:
- A setting name/label grouping is missing and impacts editor UX.
- A behavior choice changes conversion flow (sticky CTA, drawer behavior).
- A feature implies a library or performance tradeoff.
- The change affects Theme Styles or Minimum Shipping Scope.

---

## 6) Mandatory Decision Logging
Add an entry to `/docs/04_CHANGELOG_DECISIONS.md` when:
- You add/remove a section in Minimum Shipping Scope
- You change Theme Styles defaults
- You introduce a new global setting
- You add site-wide JS
- You add a third-party library
- You alter RTL/bidi primitives
- You change copy canon (07) or tokens (06) materially
- You claim compatibility status changes (COMPATIBILITY)
- You adjust support terms (SUPPORT_POLICY)

---

## 7) Stop Conditions (Block Continue)
If any occurs, stop and fix before proceeding:
- Hardcoded Hebrew UI appears (non-content)
- Drawer/modal breaks keyboard/focus behavior
- RTL icon direction wrong anywhere in shipped templates
- Visible CLS in hero/gallery/cart drawer
- Missing locale keys causing broken translation output
- Inventory registry not updated for new components

---

## 8) Definition of Done
A change is DONE only when:
- Relevant QA matrix items pass (03) OR the task is explicitly “doc-only”
- REGRESSION_CHECKLIST passes for code changes
- Translations exist (he + en + schema)
- RTL/LTR both render without breakage
- No regressions in header/cart/PDP loops
- Component registry updated if applicable (05)
- Decision log updated if required (04)

END

