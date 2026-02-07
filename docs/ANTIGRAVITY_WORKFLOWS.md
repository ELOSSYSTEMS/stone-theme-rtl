/docs/ANTIGRAVITY_WORKFLOWS.md
# ANTIGRAVITY_WORKFLOWS — Practical IDE Runbooks for Building the RTL/Hebrew Theme
Version: 0.2  
Scope: Repeatable workflows an Antigravity IDE agent can execute safely.  
Rule: Each workflow must cite its required docs and end with QA notes.

---

## 0) Operating Mode (Applies to All Workflows)
### Mandatory startup artifacts
- `/GLOBAL_ANTIGRAVITY_RULES.md`
- `/docs/CANONICAL_INDEX.md`
- `/docs/FILE_MAP.md`
- `/docs/IMPLEMENTATION_PLAN.md` (must be updated each session)

### Mandatory outputs
- Goal + touched files
- Patch (full files or anchored replacements)
- Locale updates if applicable
- Inventory/preset updates if applicable
- QA: REGRESSION_CHECKLIST minimum, QA_MATRIX when required

---

## 1) Workflow: Repo Warm-Up / Orientation
**Required docs:** GLOBAL rules, CANONICAL_INDEX, FILE_MAP, IMPLEMENTATION_PLAN  
**Steps**
1) Read mandatory startup artifacts.
2) Identify current phase (02_BUILD_ROADMAP).
3) Choose ONE objective from IMPLEMENTATION_PLAN.
4) Confirm whether decision log entry required.

---

## 2) Workflow: New Section Scaffolding (Theme Store-safe)
**Required docs:** FILE_MAP, ARCHITECTURE_CONTRACT, SCHEMA_SETTINGS_CONVENTIONS, SECTION_INVENTORY, DESIGN_TOKENS, TRANSLATION_KEYS_MAP  
**Steps**
1) Add PLANNED entry to `05_SECTION_INVENTORY.md` (or confirm exists).
2) Create `sections/<name>.liquid` with schema using `t:` keys.
3) Add schema translations (he/en schema).
4) Add storefront translations if section renders UI strings (he/en).
5) Add scoped CSS/JS only if needed.
6) Place into template JSON with safe defaults.
7) Update Section Inventory to IN_PROGRESS with settings list.
8) QA: run REGRESSION_CHECKLIST + any relevant QA_MATRIX items.

**Reusable prompt**
> Scaffold section `<name>` per SCHEMA_SETTINGS_CONVENTIONS. Use TRANSLATION_KEYS_MAP namespaces. Register it in SECTION_INVENTORY and update templates safely.

---

## 3) Workflow: Implement Israel Differentiator (Novel)
**Required docs:** MASTER_SPEC, DESIGN_TOKENS, COPY_STYLE_GUIDE_HE, PERFORMANCE_PLAYBOOK, A11Y_PLAYBOOK, SECTION_INVENTORY  
**Steps**
1) Confirm differentiator is in scope.
2) Implement as section with disable toggle and conservative defaults.
3) Ensure: no exaggerated claims, minimal JS, full i18n.
4) Register in inventory; log decision if scope-impacting.
5) QA: regression + targeted RTL/bidi checks.

---

## 4) Workflow: Template Composition / Recomposition
**Required docs:** MASTER_SPEC, THEME_STYLES_SPEC, SECTION_INVENTORY, ACCEPTANCE_CRITERIA  
**Steps**
1) Compose template section stack per style baseline.
2) Ensure referenced section types exist.
3) Validate editor loads and template renders.
4) Update THEME_STYLES_SPEC if defaults changed; log decision.
5) QA: Flow A + regression.

---

## 5) Workflow: Localization Completion Pass
**Required docs:** TRANSLATION_KEYS_MAP, COPY_STYLE_GUIDE_HE, BIDI_EDGE_CASES  
**Steps**
1) Enumerate new/changed keys.
2) Update he/en + schema he/en.
3) Verify no hardcoded system strings.
4) Apply LTR islands for mixed-direction text.
5) QA: regression + bidi string suite in key surfaces.

---

## 6) Workflow: RTL/Bidi Hardening Pass
**Required docs:** BIDI_EDGE_CASES, DESIGN_TOKENS, REGRESSION_CHECKLIST  
**Steps**
1) Run 09 string suite across header/cart/PDP/footer.
2) Fix via wrappers + isolate utilities + icon mirroring rules.
3) Re-run regression checklist.

---

## 7) Workflow: Performance Hardening Pass
**Required docs:** PERFORMANCE_PLAYBOOK, ERROR_BUDGET, KNOWN_PITFALLS  
**Steps**
1) Identify CLS hotspots: hero/gallery/cart drawer.
2) Reserve space and reduce global assets.
3) Ensure no new site-wide JS without decision log.
4) QA: regression + visual CLS check.

---

## 8) Workflow: Accessibility Hardening Pass
**Required docs:** A11Y_PLAYBOOK, COPY_STYLE_GUIDE_HE  
**Steps**
1) Ensure button semantics + aria labels.
2) Focus trap for drawers/modals; Escape closes; return focus.
3) Tab navigation passes in RTL.
4) QA: regression + keyboard smoke.

---

## 9) Workflow: Theme Styles Presets Build/Update
**Required docs:** THEME_STYLES_SPEC, ACCEPTANCE_CRITERIA, CHANGELOG_DECISIONS  
**Steps**
1) Implement style defaults (structure + settings, not just colors).
2) Update THEME_STYLES_SPEC.
3) Log decision entry (required).
4) QA: Flow A for each preset in Hebrew.

---

## 10) Workflow: Bug Fix (Triage → Patch → Regression)
**Required docs:** FILE_MAP, KNOWN_PITFALLS, REGRESSION_CHECKLIST  
**Steps**
1) Reproduce.
2) Patch minimal diff.
3) Update locales if necessary.
4) Run regression checklist.
5) Escalate to QA matrix if core flow touched.

---

## 11) Workflow: Compatibility Entry (After Real Tests)
**Required docs:** COMPATIBILITY, REGRESSION_CHECKLIST  
**Steps**
1) Test app with dev theme.
2) Run regression + key flows.
3) Record results in COMPATIBILITY. No claims without tests.

---

## 12) Workflow: Release Candidate Prep
**Required docs:** RELEASE_CHECKLIST, QA_TEST_MATRIX, SECTION_INVENTORY, THEME_STYLES_SPEC, CHANGELOG_DECISIONS  
**Steps**
1) Execute RELEASE_CHECKLIST fully.
2) Run QA matrix (Hebrew) + LTR smoke.
3) Confirm docs are consistent with behavior.
4) Produce release entry in decision log.

---

## 13) Workflow: Documentation Sync Pass
**Required docs:** CANONICAL_INDEX, README_FOR_IDE, SECTION_INVENTORY, FILE_MAP  
**Steps**
1) Reconcile Section Inventory vs repo files.
2) Ensure CANONICAL_INDEX lists all docs accurately.
3) Ensure README_FOR_IDE references all operational docs.
4) QA: doc-only changes (no code).

---

## 14) Workflow: Add New Doc to Governance
**Required docs:** CANONICAL_INDEX, README_FOR_IDE, CHANGELOG_DECISIONS (if scope-affecting)  
**Steps**
1) Create doc under `/docs/`.
2) Add it to CANONICAL_INDEX.
3) Add it to README_FOR_IDE (as canonical or operational).
4) Log decision only if it changes authority/scope rules.

END

