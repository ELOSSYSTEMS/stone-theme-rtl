# IDE Prompt Library — “WMW-style” Delivery (Copy/Paste)

Use these prompts to get your IDE/LLM to behave like a seasoned Shopify Plus agency.
Pattern: Planning-only first → small safe diffs → strict QA → decision log.

---

## Prompt 1 — Build the Delivery Plan
Mode: PLANNING
Objective: Produce a milestone plan to build an RTL-first, Hebrew-first Shopify theme on Shopify CLI skeleton, optimized for performance and accessibility.
Constraints:
- RTL-first and bidi-safe
- i18n-first (he/en)
- No global JS unless justified
- Every change must list QA steps
Output contract:
- Goal
- Files touched (TBD if unknown)
- Assumptions (minimal)
- Milestones (Discovery → Design/Dev → QA → Post-launch)
- Risks + mitigations
Stop conditions:
- If any canonical paths are unknown, stop and ask for repo map.

---

## Prompt 2 — Section Library Inventory
Mode: PLANNING
Objective: Define a section inventory and schema design that can power 80% of typical stores, with RTL/i18n constraints.
Include:
- Section list (hero, collection grid, product media, trust, FAQ, footer, header, etc.)
- For each: settings, blocks, defaults, i18n approach, RTL considerations (logical properties, icon mirroring)
Output contract:
- Section table
- Schema patterns
- Accessibility notes
Stop conditions:
- If you need to change layout/theme.liquid or templates JSON, require rollback plan.

---

## Prompt 3 — RTL + CSS Architecture Rules
Mode: PLANNING
Objective: Produce a set of CSS and component rules implementing WMW’s public RTL guidance using CSS logical properties and direction switching.
Must include:
- Logical properties checklist
- “LTR islands” rules
- Mirroring rules for icons/arrows
- Typography strategy for Hebrew + Latin fallback
Output contract:
- Rulebook + examples
- QA checks (visual, keyboard, focus order)
Stop conditions:
- If any rule requires external libs, justify and propose minimal alternative.

---

## Prompt 4 — Checkout Extensibility Boundary
Mode: PLANNING
Objective: Define boundaries between theme responsibilities and checkout customization responsibilities using Checkout Extensibility primitives.
Must include:
- What stays in theme vs what becomes UI extensions/Functions/Branding API/Web Pixels
- Migration strategy if checkout.liquid exists
Output contract:
- Boundary diagram (text) + acceptance criteria
Stop conditions:
- If merchant plan constraints are unknown, state UNKNOWN and avoid hard claims.

---

## Prompt 5 — Execution Slice Template (Small Diff)
Mode: EXECUTION
Objective: Implement ONE small section (e.g., RTL-safe Announcement Bar) with schema, locales (he/en), and a11y.
Allowed files: (explicit paths after repo map confirmed)
Output contract:
- Files touched
- Patch format (full files or anchored replacements)
- Locale updates (he/en)
- QA steps + what remains untested
- Decision log: YES
Stop conditions:
- If it requires touching layout/theme.liquid, stop and return to planning.

