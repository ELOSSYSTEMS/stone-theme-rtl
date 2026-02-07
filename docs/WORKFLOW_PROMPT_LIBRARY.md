/docs/WORKFLOW_PROMPT_LIBRARY.md
# WORKFLOW_PROMPT_LIBRARY — Copy/Paste Prompts for Antigravity IDE
Version: 0.1  
Goal: “Install” workflows by providing deterministic, reusable prompts.  
Rule: Each run = one objective.  
Rule: Two-Hat Protocol enforced (PLANNING default, EXECUTION only after approval).  
Rule: Output must follow README_FOR_IDE output contract + GLOBAL rules.

---

## 0) Global Header (Paste Above Any Workflow Prompt)
Use this header for every run.

Mode: PLANNING (default) or EXECUTION (only after approval)  
Objective: <single sentence>  
Allowed files: <explicit paths>  
Phase: <from 02_BUILD_ROADMAP.md>  
QA requirement: `/docs/REGRESSION_CHECKLIST.md` minimum; `/docs/03_QA_TEST_MATRIX.md` when core flows affected  
Stop conditions: follow `/GLOBAL_ANTIGRAVITY_RULES.md`  

Mandatory docs to open first:
- `/GLOBAL_ANTIGRAVITY_RULES.md`
- `/docs/README_FOR_IDE.md`
- `/docs/CANONICAL_INDEX.md`
- `/docs/FILE_MAP.md`
- `/docs/IMPLEMENTATION_PLAN.md`

---

## 1) START SESSION — Orientation + Plan Update (Docs-only)
Mode: PLANNING  
Objective: Orient to repo and update Next 3 objectives.

Allowed files:
- `/docs/IMPLEMENTATION_PLAN.md`
- `/docs/CANONICAL_INDEX.md` (if needed)
- `/docs/README_FOR_IDE.md` (if needed)

Steps:
1) Confirm current phase from `02_BUILD_ROADMAP.md`.
2) Update `IMPLEMENTATION_PLAN.md`:
   - set Current Phase
   - fill Objective 1/2/3 with goal, target files, QA items
3) Output:
   - Updated full file(s) content
   - Any blockers as explicit questions

Hard prohibition:
- No edits to theme code.

---

## 2) NEW SECTION SCAFFOLD — Theme Store-safe (Exec candidate)
Mode: PLANNING  
Objective: Produce an implementation plan for a new section `<section_name>`.

Required docs:
- `/docs/01_ARCHITECTURE_CONTRACT.md`
- `/docs/SCHEMA_SETTINGS_CONVENTIONS.md`
- `/docs/TRANSLATION_KEYS_MAP.md`
- `/docs/05_SECTION_INVENTORY.md`

Deliverable (PLANNING):
- A short plan specifying:
  - section file path
  - schema fields (grouped)
  - translation namespaces + key list
  - whether CSS/JS required (and where referenced)
  - templates impacted (if any)
  - QA items

Stop:
- Request user approval to switch to EXECUTION.

EXECUTION prompt (use only after approval):
Mode: EXECUTION  
Objective: Implement new section `<section_name>` as specified in the approved plan.

Allowed files (example):
- `sections/<section_name>.liquid`
- `templates/<x>.json` (only if required)
- `locales/he.json`, `locales/en.default.json`
- `locales/he.schema.json`, `locales/en.default.schema.json`
- `/docs/05_SECTION_INVENTORY.md`
- `/docs/04_CHANGELOG_DECISIONS.md` (only if scope/preset changes)

Output must include:
- Objective header + file paths
- Full file contents or anchored replacements
- Locale key additions (all 4 locales if schema/user strings touched)
- Inventory update
- QA steps (REGRESSION_CHECKLIST + relevant QA_MATRIX items)

---

## 3) TEMPLATE COMPOSITION — Build/Adjust a JSON Template
Mode: PLANNING  
Objective: Plan composition changes for `templates/<name>.json`.

Required docs:
- `/docs/08_THEME_STYLES_SPEC.md`
- `/docs/05_SECTION_INVENTORY.md`
- `/docs/ACCEPTANCE_CRITERIA.md`

Deliverable (PLANNING):
- Proposed section stack (top → bottom)
- Default settings strategy (minimal, premium defaults)
- Risk notes (missing sections, editor load risk)
- QA plan

EXECUTION (after approval):
Allowed files:
- `templates/<name>.json`
- `/docs/08_THEME_STYLES_SPEC.md` (if defaults change)
- `/docs/04_CHANGELOG_DECISIONS.md` (if preset/default behavior changes)

Output:
- Full updated JSON
- Verification: all section types exist
- QA: regression + Flow A for impacted page

---

## 4) LOCALIZATION PASS — Keys + Completeness
Mode: PLANNING  
Objective: Plan and enumerate missing translation keys for touched components.

Required docs:
- `/docs/TRANSLATION_KEYS_MAP.md`
- `/docs/07_COPY_STYLE_GUIDE_HE.md`
- `/docs/09_BIDI_EDGE_CASES.md`

Deliverable (PLANNING):
- Table: key → where used → he value → en value → schema?
- Identify bidi-sensitive strings requiring LTR islands

EXECUTION (after approval):
Allowed files:
- `locales/he.json`, `locales/en.default.json`
- `locales/he.schema.json`, `locales/en.default.schema.json`

Output:
- Full diffs / updated blocks
- Confirm no hardcoded strings remain
- QA: regression + bidi suite in header/cart/PDP surfaces

---

## 5) RTL/BIDI HARDENING — Mixed Direction Stability
Mode: PLANNING  
Objective: Identify bidi breakpoints in `<components>`.

Required docs:
- `/docs/09_BIDI_EDGE_CASES.md`
- `/docs/06_DESIGN_TOKENS.md`
- `/docs/KNOWN_PITFALLS.md`

Deliverable (PLANNING):
- List of locations + fix pattern per location
- Which wrappers/utilities to apply

EXECUTION (after approval):
Allowed files:
- only the component files listed in the plan

Output:
- Patch
- Confirm icon mirroring and LTR islands
- QA: regression + bidi suite strings

---

## 6) PERFORMANCE PASS — CLS + Asset Scoping
Mode: PLANNING  
Objective: Identify CLS and asset-scope violations in `<page/components>`.

Required docs:
- `/docs/10_PERFORMANCE_PLAYBOOK.md`
- `/docs/ERROR_BUDGET.md`
- `/docs/KNOWN_PITFALLS.md`

Deliverable (PLANNING):
- CLS suspects list + mitigation steps
- Asset scope changes proposed (global → component)
- Risk notes

EXECUTION (after approval):
Allowed files:
- only files listed in plan
- decision log if site-wide JS/CSS changes

Output:
- Patch
- Explicit statement about CLS mitigation applied
- QA: regression + visual CLS check on hero/gallery/cart drawer

---

## 7) A11Y PASS — Focus + Keyboard + ARIA
Mode: PLANNING  
Objective: Audit `<component>` for a11y compliance.

Required docs:
- `/docs/11_A11Y_PLAYBOOK.md`
- `/docs/ACCEPTANCE_CRITERIA.md`

Deliverable (PLANNING):
- Findings list
- Proposed fixes with minimal diffs

EXECUTION (after approval):
Allowed files:
- only component files listed

Output:
- Patch
- A11y checklist confirmation
- QA: keyboard smoke + regression

---

## 8) BUG FIX — Triage → Minimal Patch → Regression
Mode: PLANNING  
Objective: Reproduce and propose fix for `<bug>`.

Required docs:
- `/docs/FILE_MAP.md`
- `/docs/KNOWN_PITFALLS.md`
- `/docs/REGRESSION_CHECKLIST.md`

Deliverable (PLANNING):
- Repro steps
- Root cause hypothesis
- Minimal patch plan
- QA plan

EXECUTION (after approval):
Allowed files:
- only files listed in plan

Output:
- Patch
- QA results (regression checklist)
- Note any remaining unknowns

---

## 9) DOC SYNC — Prevent Drift (Docs-only)
Mode: PLANNING  
Objective: Reconcile docs with current repo state.

Allowed files:
- `/docs/*` only

Steps:
1) Reconcile `05_SECTION_INVENTORY` vs existing sections/snippets.
2) Update `CANONICAL_INDEX` if docs added/removed.
3) Ensure `README_FOR_IDE` operational docs list matches reality.

Output:
- Full updated docs
- No code changes

---

## 10) RC PREP — Release Candidate Readiness
Mode: PLANNING  
Objective: Prepare RC checklist and identify blockers.

Required docs:
- `/docs/RELEASE_CHECKLIST.md`
- `/docs/03_QA_TEST_MATRIX.md`
- `/docs/REGRESSION_CHECKLIST.md`
- `/docs/04_CHANGELOG_DECISIONS.md`

Deliverable (PLANNING):
- RC readiness report: PASS/FAIL/UNKNOWN per checklist item
- Blockers list
- Proposed “RC fix queue” as next objectives in IMPLEMENTATION_PLAN

EXECUTION:
Only after explicit approval per fix objective.

END

