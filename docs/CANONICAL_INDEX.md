# CANONICAL_INDEX — Map of Governing Documents (Single Entry Point)
Version: 0.3
Rule: This file is the map. Keep it current.
Rule: Any new doc that influences build behavior must be listed here.
Rule: `/docs/` is binding. `/knowledge_base/` is advisory.

---

## 0) Definitions
### 0.1 Precedence Canon
Documents that can override other docs.
Precedence order is defined in:
- `/GLOBAL_ANTIGRAVITY_RULES.md`
- `/docs/README_FOR_IDE.md`

### 0.2 Operational Mandatory Docs
Documents that do not override Tier A/B/C, but are required to execute correctly and quickly.

---

## 1) Authority Tiers
- Tier A (Hard Authority): scope, architecture, tokens, copy, bidi, perf, a11y
- Tier B (Execution/Validation): roadmap, QA matrix, inventory, styles, changelog
- Tier C (Customer Truth): support, compatibility

---

## 2) Canonical Docs Table
| Tier | Path | Owns Decisions About | “Change Requires Log?” |
|---|---|---|---|
| A | `/docs/00_MASTER_SPEC.md` | Product scope, non-negotiables, minimum shipping set | YES |
| A | `/docs/01_ARCHITECTURE_CONTRACT.md` | Repo structure, coding rules, i18n/RTL rules | YES |
| A | `/docs/06_DESIGN_TOKENS.md` | Spacing/type/rhythm/buttons/forms/icons | YES |
| A | `/docs/07_COPY_STYLE_GUIDE_HE.md` | Hebrew microcopy canon + terminology | YES |
| A | `/docs/09_BIDI_EDGE_CASES.md` | RTL/bidi primitives + LTR islands | YES |
| A | `/docs/10_PERFORMANCE_PLAYBOOK.md` | Performance patterns + CLS prevention | YES |
| A | `/docs/11_A11Y_PLAYBOOK.md` | Accessibility patterns + focus rules | YES |
| B | `/docs/02_BUILD_ROADMAP.md` | Phases + sequencing + “next tasks” | NO |
| B | `/docs/03_QA_TEST_MATRIX.md` | Test requirements + done gates | NO |
| B | `/docs/05_SECTION_INVENTORY.md` | Component registry, settings lists, deps | YES (if adding/removing) |
| B | `/docs/08_THEME_STYLES_SPEC.md` | Presets for verticals | YES |
| B | `/docs/04_CHANGELOG_DECISIONS.md` | Decision record + version notes | N/A |
| C | `/docs/SUPPORT_POLICY.md` | Customer support boundaries | YES |
| C | `/docs/COMPATIBILITY.md` | Tested apps + conflicts | YES |

---

## 3) Operational Mandatory Docs (Required)
- `/docs/FILE_MAP.md` (Exists)
- `/docs/IMPLEMENTATION_PLAN.md` (Canonical Plan) (Exists)
- `/docs/ACCEPTANCE_CRITERIA.md` (Exists)
- `/docs/TRANSLATION_KEYS_MAP.md` (Exists)
- `/docs/SCHEMA_SETTINGS_CONVENTIONS.md` (Exists)
- `/docs/ERROR_BUDGET.md` (Exists)
- `/docs/REGRESSION_CHECKLIST.md` (Exists)
- `/docs/KNOWN_PITFALLS.md` (Exists)
- `/docs/RELEASE_CHECKLIST.md` (Exists)
- `/docs/ANTIGRAVITY_WORKFLOWS.md` (Exists)
- `/docs/README_FOR_IDE.md` (Exists)
- `/GLOBAL_ANTIGRAVITY_RULES.md` (Planned)

---

## 4) Non-Canonical Reference (Advisory / Context Only)
> Rule: Reference only. Not requirements unless promoted into a canonical doc and logged.

- `/docs/### Solo Build Playbook.md`
- `/docs/Shopify CLI Official Documentation Map and Inventory.md`
- `/docs/Novel Sections - Blocks.md`
- `/docs/WORKFLOW_RUNNER.md`
- `/docs/WORKFLOW_PROMPT_LIBRARY.md`
- `/docs/MASTER_THEME_SPEC - Hebrew-First RTL.txt`

---

## 5) Deprecated / Archive
- `/docs/archive/Build Roadmap.md` (Merged into 00_MASTER_SPEC)
- `/docs/archive/INTIAL_IMPLEMENTATION_PLAN.md` (Merged into IMPLEMENTATION_PLAN)

END
