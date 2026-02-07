# IDE Prompt Library — Vendor-grade workflow (copy/paste)

These prompts force your IDE/LLM to behave like a top-tier theme maker:
- small diffs
- clear constraints
- upgrade safety
- strict QA

---

## Prompt A — Build a doctrine-first plan (PLANNING)
Mode: PLANNING
Objective: Produce a doctrine-first delivery plan for a Skeleton-based Shopify theme that remains upgradeable over time.
Constraints:
- Avoid global refactors
- Prefer settings/schema over code edits
- RTL-first + i18n-first (he/en)
- JS is progressive enhancement; section-scoped only
Output contract:
- Goal
- Milestones
- Risks (updates, apps, a11y, CLS)
- File zones classification (high/medium/low risk)
- QA matrix for each milestone
Stop conditions:
- If repo paths are unknown, stop and request a file map.

---

## Prompt B — Design the “extension points” (PLANNING)
Mode: PLANNING
Objective: Define extension points so merchants can customize without code edits.
Must include:
- Custom Liquid section
- Custom CSS injection strategy (bounded)
- Integration hooks (events/snippets)
Output contract:
- Extension point list
- Where they live
- Guardrails and examples
Stop conditions:
- If changes require `layout/theme.liquid`, require rollback plan and approval.

---

## Prompt C — One section, fully compliant (EXECUTION)
Mode: EXECUTION
Objective: Implement ONE RTL-safe section with full schema + he/en locale strings + keyboard accessibility.
Allowed files: TBD until canonical paths confirmed
Output contract:
- Files touched
- Patch format
- Locale updates (he/en)
- QA steps (mobile/desktop/RTL/LTR islands/keyboard/CLS)
Decision log: YES
Stop conditions:
- If scope expands beyond the single section, stop and return to planning.

