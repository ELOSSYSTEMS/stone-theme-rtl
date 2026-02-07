/docs/WORKFLOW_RUNNER.md
# WORKFLOW_RUNNER — Which Prompt to Use (Fast Router)
Version: 0.1  
Goal: Reduce IDE wandering. Pick the right workflow prompt in <30 seconds.

---

## 0) Always Start Here
If starting a session or unclear state:
- Use Prompt: **START SESSION — Orientation + Plan Update**

---

## 1) Task → Workflow Mapping
### A) You need to build a new component
Use:
- **NEW SECTION SCAFFOLD — Theme Store-safe**

### B) You need to change page layout / stacks
Use:
- **TEMPLATE COMPOSITION — Build/Adjust a JSON Template**

### C) You added/changed copy or schema labels, or translations are missing
Use:
- **LOCALIZATION PASS — Keys + Completeness**

### D) Mixed Hebrew/English breaks, numbers reorder, arrows wrong direction
Use:
- **RTL/BIDI HARDENING — Mixed Direction Stability**

### E) Page shifts when loading, feels slow, too much global CSS/JS
Use:
- **PERFORMANCE PASS — CLS + Asset Scoping**

### F) Drawer/modal/accordion is not keyboard-friendly or focus breaks
Use:
- **A11Y PASS — Focus + Keyboard + ARIA**

### G) A specific bug exists and you want minimal patch + regression
Use:
- **BUG FIX — Triage → Minimal Patch → Regression**

### H) Docs are drifting or new docs were added
Use:
- **DOC SYNC — Prevent Drift (Docs-only)**

### I) Preparing to submit / release candidate
Use:
- **RC PREP — Release Candidate Readiness**

---

## 2) Two-Hat Enforcement (Reminder)
- Start in PLANNING.
- Switch to EXECUTION only after user approval of the plan.
- One objective per run.

---

## 3) Default QA
- After any code change: `/docs/REGRESSION_CHECKLIST.md`
- For core flows or releases: `/docs/03_QA_TEST_MATRIX.md`

END

