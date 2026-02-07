/GLOBAL_ANTIGRAVITY_RULES.md
# GLOBAL_ANTIGRAVITY_RULES — Antigravity / LLM Operating Contract (RTL Hebrew-First Theme Repo)
Version: 2.2
Owner: RTL Hebrew-First Theme (Theme Store eligible)
Risk default: Medium | Fail-closed on ambiguity
Prime posture: Safety + determinism + auditability

---

## 0) Prime Directive
No destructive or high-risk action is allowed unless a verified rollback exists.
If rollback is not verified → STOP.

High-risk actions include:
- bulk refactors, renames/moves/deletes
- migrations/sync overwrites
- theme push/pull to Shopify
- edits to `templates/*.json`, `config/*`, `layout/theme.liquid`
- introducing site-wide JS/CSS or third-party libraries

---

## 1) Authority & Precedence (Canonical Truth)
### 1.1 Canonical Document Precedence (Highest → Lowest)
**Rule: `/docs/` overrides `/knowledge_base/` always.**
**Rule: `/knowledge_base/` is advisory only.**

1) `/docs/00_MASTER_SPEC.md`
2) `/docs/01_ARCHITECTURE_CONTRACT.md`
3) `/docs/06_DESIGN_TOKENS.md`
4) `/docs/07_COPY_STYLE_GUIDE_HE.md`
5) `/docs/09_BIDI_EDGE_CASES.md`
6) `/docs/10_PERFORMANCE_PLAYBOOK.md`
7) `/docs/11_A11Y_PLAYBOOK.md`
8) `/docs/02_BUILD_ROADMAP.md`
9) `/docs/03_QA_TEST_MATRIX.md`
10) `/docs/05_SECTION_INVENTORY.md`
11) `/docs/08_THEME_STYLES_SPEC.md`
12) `/docs/04_CHANGELOG_DECISIONS.md`
13) `/docs/SUPPORT_POLICY.md`
14) `/docs/COMPATIBILITY.md`

If any instruction conflicts, the higher document wins.

### 1.2 Single Source of Change (Workspace Rule)
Only ONE canonical workspace exists per theme at a time.
- Canonical theme workspace path: `/theme/<THEME_NAME>/`
- Any other folder is non-canonical until explicitly promoted via decision log entry.

“Canonical” means:
- Git tracked
- Clean working tree before risky operations
- Remote exists
- Backups exist (Section 3)

---

## 2) Start-of-Session Checklist (Mandatory)
Before any code work:
1) Open/read: `/docs/CANONICAL_INDEX.md`
2) Open/read: `/docs/FILE_MAP.md`
3) Open/update: `/docs/IMPLEMENTATION_PLAN.md` (Next 3 objectives)
4) Confirm mode: PLANNING (default) or EXECUTION (only after approval)

---

## 3) Work Mode (Deterministic Execution)
### 3.1 One Objective Per Run
Each agent run must have exactly one objective.
If multiple are requested, split runs.

### 3.2 No Improvisation
Do not invent scope, settings structure, Hebrew microcopy, or architecture.
If required inputs are missing → STOP.

### 3.3 No Silent Scope Creep
No “helpful extras” beyond the approved objective.

---

## 4) Backup Policy (Required Before Any Risk)
Before any high-risk action, produce ALL 3 backups:

A) Git checkpoint
- Commit: `checkpoint: <what> (pre-change)`
- Tag: `cp-YYYYMMDD-HHMM-<slug>`

B) Local archive
- Zip canonical theme dir:
  - `theme_<name>_YYYYMMDD-HHMM.zip`
- Store: `/backups/theme/`

C) Shopify duplicate (when Shopify involved)
- Duplicate theme in Shopify Admin
- Name: `CP YYYY-MM-DD HH:MM - <slug>`

Verification:
- Confirm zip opens and contains:
  - `assets/`, `sections/`, `snippets/`, `templates/`, `config/`, `layout/`, `locales/`

If any step cannot be completed → STOP.

---

## 5) Git Discipline (Non-Negotiable)
- `main` = last known good
- `dev` = active work
- `mig/*` = migration/sync/port only

Rules:
- No high-risk work unless `git status` clean.
- Small commits; >20 files requires manifest (Section 8).
- Never force-push to `main`.

---

## 6) Shopify Theme Safety Rules
1) Never edit production theme directly.
2) Always work against a dev theme ID.
3) Keep Shopify duplicate:
   - `GOLDEN - last stable`
4) Push in small batches; verify in editor after each batch.

Break-glass LIVE push only if user provides:
- `OVERRIDE_LIVE_PUSH: YES`
- `LIVE_THEME_ID: <id>`
- `REASON: <short>`
- `ROLLBACK_THEME: GOLDEN - last stable`

Missing any → STOP.

---

## 7) Sync / Push / Pull Rules
- Never sync unless you can state direction in one sentence.
- Before sync: backups + diff review.
- After sync: REGRESSION_CHECKLIST + core smoke.
- If uncertain: partial push or dry-run diff.

---

## 8) File Manifest Requirement
If you are about to:
- port from another folder/repo
- apply patches across many files
- recreate state

You must create:
- `/docs/MIGRATION_MANIFEST.md`

Must include:
- source/destination paths
- explicit file list + add/update/delete counts
- dependency notes

No silent missing deps allowed.

---

## 9) Template & Section Integrity
- Every JSON section type referenced must exist.
- Avoid renaming section types; prefer additive changes.
- Theme editor must load templates without errors.

---

## 10) Liquid Safety Rules
- Guard null objects.
- Snippets render safely alone.
- Blocks tolerate missing settings with defaults.

---

## 11) Asset Safety Rules
- New JS/CSS referenced intentionally (global or per-section).
- No unscoped global selectors.
- If JS fails, page remains navigable.

---

## 12) Output Contract
Every implementation output must include:
- Goal + file paths
- Patch (full files or anchored replacements)
- Locale updates if applicable
- RTL/bidi confirmations
- Perf + a11y confirmations
- Inventory/preset updates if applicable
- QA steps:
  - default: `/docs/REGRESSION_CHECKLIST.md`
  - full gates: `/docs/03_QA_TEST_MATRIX.md` when required

---

## 13) Diff Review Checklist
Before:
- list touched files
- confirm no accidental deletes
- confirm critical files touched only intentionally

After:
- search for broken references: render/asset_url/section types

---

## 14) Smoke Test Checklist (Must Pass)
Minimum after any code batch on dev theme:
- Run `/docs/REGRESSION_CHECKLIST.md`

If any fail → rollback protocol.

---

## 15) Rollback Protocol
1) Switch Shopify to `GOLDEN - last stable` (if Shopify affected)
2) Reset local to last checkpoint tag
3) Re-apply in smaller batches with manifests

---

## 16) Documentation Stewardship
- No silent behavioral changes without doc updates.
- Keep `README_FOR_IDE` and `CANONICAL_INDEX` current.

---

## 17) Stop Conditions
Stop immediately if:
- change can’t be described in one sentence
- backups missing for a high-risk action
- unexplained deletions
- template fails to load in editor
- missing referenced snippet/asset
- RTL/bidi uncertain and untested

---

## 18) Two-Hat Protocol (Enforced)
Default mode: PLANNING.

PLANNING:
- no functional code edits
- produce plan/doc updates
- request approval

EXECUTION:
- only after explicit approval
- execute only approved plan
- if flaw found: revert to PLANNING

END

