/docs/04_CHANGELOG_DECISIONS.md
# 04_CHANGELOG_DECISIONS — Decision Log + Changelog (Immutable Record)
Version: 0.1  
Rule: Every non-trivial decision or scope change gets an entry.  
Format: Append-only. Do not rewrite history. If something changes, add a new entry.

---

## 0) How to Use This File
Use this for:
- Scope adds/removals
- Architecture rule exceptions
- Third-party library adoption
- Preset/style changes
- Breaking changes
- Known issues and planned fixes

---

## 1) Entry Template (Copy/Paste)
### [YYYY-MM-DD] DECISION: <short title>
**Type:** Decision | Changelog | Breaking | Risk | Known Issue  
**Owner:** Allon / IDE / Assistant  
**Context:** What problem triggered this?  
**Decision:** What was chosen (clear and specific).  
**Alternatives Considered:** 2–3 options with why rejected.  
**Tradeoffs:** What we gain / what we lose.  
**Impact Radius:**
- Templates affected:
- Sections/blocks affected:
- Locales affected:
- Performance/A11y impact:
**QA Requirements:** Which QA matrix items must be re-run.  
**Follow-ups:** Concrete next tasks with file paths.  
**Status:** Proposed | Approved | Implemented | Reverted

---

## 2) Release Versioning Policy
- v0.x: pre-release development
- v1.0: Theme Store submission candidate
- Patch releases: bug fixes only (no breaking setting/schema changes)
- Minor releases: new sections/features (non-breaking)
- Major releases: breaking changes (must include migration notes)

---

## 3) Mandatory Logging Events
Log an entry when:
- You add/remove a section in Minimum Shipping Scope
- You change any Theme Style preset defaults
- You add a new global setting
- You introduce JS that runs site-wide
- You adopt any third-party library
- You decide to drop blog/article templates
- You alter RTL/bidi core rules
- You change support policy assumptions

---

## 4) Known Issues (Active)
(Keep current. Each item must reference a decision entry.)
- None

---

## 5) Decisions (Chronological)
### [2026-02-07] DECISION: Initialize governance docs
**Type:** Decision  
**Owner:** Allon / Assistant  
**Context:** Need canonical docs to govern IDE-driven theme build.  
**Decision:** Create 5 canonical docs: 00_MASTER_SPEC, 01_ARCHITECTURE_CONTRACT, 02_BUILD_ROADMAP, 03_QA_TEST_MATRIX, 04_CHANGELOG_DECISIONS.  
**Alternatives Considered:** Ad hoc instructions (rejected: drift risk).  
**Tradeoffs:** More upfront writing; far less rework.  
**Impact Radius:** All development processes.  
**QA Requirements:** N/A  
**Follow-ups:** Keep “Next 3 Tasks” updated in 02_BUILD_ROADMAP.md.  
**Status:** Implemented

### [2026-02-07] DECISION: Governance & Docs consolidation
**Type:** Decision
**Owner:** Allon / Assistant
**Context:** Docs were fragmented (`/_docs/` vs `/docs/` - Legacy paths), redundant (roadmaps), and lacked clear authority structure.
**Decision:**
1.  **Enforce `/docs/`**: Removed `/_docs/` (Legacy path) and references.
2.  **Consolidate Roadmap**: Merged `Build Roadmap.md` into `00_MASTER_SPEC.md`; `02_BUILD_ROADMAP.md` is now sole authority.
3.  **Consolidate Plan**: Merged typo file `INTIAL_...` into `IMPLEMENTATION_PLAN.md`.
4.  **KB Governance**: Created `/knowledge_base/` root governance to distinguish "advisory" vs "binding".
**Status:** Implemented

### [2026-02-07] DECISION: Update Global Rules to v2.2
**Type:** Decision
**Owner:** Allon / Assistant
**Context:** `GLOBAL_ANTIGRAVITY_RULES.md` lacked explicit precedence rules for the new `/knowledge_base/`.
**Decision:** Updated to v2.2 to explicitly state:
1. `/docs/` overrides `/knowledge_base/` always.
2. `/knowledge_base/` is advisory only.
**Status:** Implemented

END

