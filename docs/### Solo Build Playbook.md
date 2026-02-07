# STONE THEME — Solo Build Playbook (Vision → Theme)

## Purpose
Build and ship an RTL/Hebrew-first Shopify theme as a solo founder by running an AI-assisted engineering workflow:
- You = Product Architect + Approver + QA gate
- IDE/LLM = Implementer (writes code), never decides scope
- This document = your operating manual

---

## Operating Principle
**You do not “learn to code.” You run a controlled software factory.**

The factory converts:
**Vision → Specifications → Plans → Executed patches → Verification → Release**

If any step is skipped, the project drifts and breaks.

---

## Roles & Responsibilities

### You (Owner)
- Define outcomes and constraints
- Decide priorities and tradeoffs
- Approve/reject plans
- Verify on preview + checklist
- Maintain governance docs

### LLM / IDE (Implementer)
- Produces plans from your specs
- Applies file changes only within allowed scope
- Provides patches + QA steps
- Stops when ambiguity or risk arises

---

## The Core Stack (Conceptual)
You only need to understand responsibilities, not syntax.

### Theme file types (conceptual)
- `.liquid` — templates + dynamic rendering
- `.json` — template configuration (OS2)
- `.css` — layout, typography, RTL behavior (prefer logical properties)
- `.js` — interactions; keep minimal and scoped

### Verification (non-negotiable)
- Static checks (Theme Check)
- Local preview
- Manual QA + regression checklist
- Performance and accessibility sanity

---

## The Solo-Safe Workflow (Daily Loop)

### Step 0 — Define a single objective
One objective per run. No multi-feature batches.

### Step 1 — Write the spec (your job)
Use the Spec Template below.

### Step 2 — Planning (LLM/IDE)
Request a PLANNING output:
- goal restated
- files touched
- assumptions (minimal)
- patch approach
- QA steps
- stop conditions

### Step 3 — Gate (your approval)
Only two outcomes:
- APPROVE (move to EXECUTION)
- REVISE/REJECT (iterate spec/plan)

### Step 4 — Execution (LLM/IDE)
Apply patches exactly as approved.

### Step 5 — Verify (your job)
Preview + checklists. If fails: revert or patch.

### Step 6 — Release
Promote from dev → stage → production using a controlled publish process.

---

## Spec Template (You Fill This In)
Copy/paste and fill. Keep it strict.

### Spec
**Objective (single sentence):**

**Scope (what’s included):**
- 

**Out of scope (explicitly excluded):**
- 

**Constraints (must hold):**
- RTL-first
- Hebrew-first / i18n-first
- No unexpected layout shifts (avoid CLS)
- Avoid global JS (prefer section-scoped)
- A11y: keyboard + focus visible + semantic structure

**Inputs / references:**
- Screenshots / examples:
- Links (optional):
- Existing section/template names (if known):

**Acceptance criteria (testable):**
- [ ] 
- [ ] 
- [ ] 

**Risks / sensitive areas:**
- [ ] 

**Rollback plan (must be simple):**
- Revert files:
- Restore previous version/tag:

---

## High-Risk Zones (Do Not Auto-Approve)
Any plan touching these requires stricter review and smaller diffs:
- `layout/theme.liquid`
- `templates/*.json`
- `config/*`
- `locales/*`

Default posture: **fail-closed** if unclear.

---

## RTL + Hebrew Doctrine (Rules to Enforce)

### RTL-first layout rules
- Prefer CSS logical properties:
  - `margin-inline`, `padding-inline`, `inset-inline`, `border-inline`
- Avoid hardcoded `left/right` unless isolated and justified
- Mirror directional icons where meaning implies direction

### LTR islands (bidi safety)
Content that often must remain LTR even inside RTL:
- numbers, prices, SKUs
- emails, URLs
- Latin brand names
Rules:
- isolate LTR islands with `dir="ltr"` as needed
- avoid bidi confusion by isolating inline segments

### Typography / readability (Hebrew-first)
- Define a consistent type scale
- Ensure line-height and spacing read well in Hebrew
- Avoid overly tight tracking

---

## Performance Doctrine (Guardrails)
- Avoid adding global JS unless essential
- Prefer:
  - CSS-first interactions where possible
  - section-scoped JS loaded only where needed
- Prevent CLS:
  - reserve image/media space
  - avoid layout-affecting late loads
- Keep DOM and assets lean

---

## Accessibility Doctrine (Minimum Bar)
Every feature must satisfy:
- keyboard navigable
- visible focus states
- appropriate roles/labels
- no trap in modals/menus
- logical tab order in RTL layouts

---

## Failure Patterns (Red Flags)
If the IDE says any of the following, slow down and reduce scope:
- “Refactored broadly”
- “Reorganized structure”
- “Simplified globally”
- “Optimized across the theme”
- “Updated many files for consistency”

Preferred: small, reversible diffs.

---

## QA Checklist (Per Feature)
Minimum checks before moving on:
- [ ] Works on mobile viewport
- [ ] Works on desktop viewport
- [ ] RTL alignment correct across key sections
- [ ] LTR islands render correctly (prices/SKUs/URLs)
- [ ] Keyboard navigation works
- [ ] No obvious CLS during load/interactions
- [ ] No console errors
- [ ] No unexpected global side effects

---

## Regression Checklist (Release Gate)
Run before publishing to production:
- [ ] Home: header/nav, hero, featured products
- [ ] Collection: filtering/sorting, pagination
- [ ] Product: gallery, variant selection, add-to-cart
- [ ] Cart: quantity changes, notes (if any), checkout link
- [ ] Search: results + empty state
- [ ] Footer: links, policies
- [ ] Localization: he/en switch (if supported)
- [ ] RTL: core pages visually coherent
- [ ] A11y: keyboard across menus/modals
- [ ] Performance sanity: no obvious regressions

---

## 30-Day Roadmap (Default Plan)

### Week 1 — Foundation
- Freeze doctrine and file conventions
- Define preset strategy (typography/color/layout)
- Establish QA/regression gates

### Week 2 — Skeleton (structure first)
- Header
- Footer
- Product page structure
- Collection page structure

### Week 3 — Systems
- Typography system + tokens
- Color tokens
- Layout presets
- Mobile spacing rules

### Week 4 — Polish & Hardening
- Performance passes
- Accessibility fixes
- Edge cases
- Integrations (apps/analytics) only after stability

---

## Decision Log (Keep This Updated)
Record major choices so you don’t re-litigate them.

### Entries
- Date:
  - Decision:
  - Why:
  - Tradeoff:
  - Impacted areas:
  - Rollback:

---

## Your Golden Rule
**No spec → no plan. No plan approval → no execution. No verification → no release.**

