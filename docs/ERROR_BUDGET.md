/docs/ERROR_BUDGET.md
# ERROR_BUDGET — Hard Budgets & Limits (Performance + Complexity)
Version: 0.1  
Goal: Keep the theme fast, stable, and Theme Store eligible by limiting complexity.

## 0) Budgets Are Defaults
These are guardrails. If you need to exceed a budget:
- you must log a decision with justification and mitigation.

## 1) Complexity Budgets
- No single section schema should exceed:
  - 25 settings (soft limit)
  - 8 blocks (soft limit)
- No template should include:
  - > 12 sections by default on mobile (soft limit)

## 2) JavaScript Budgets
- Avoid site-wide JS.
- If site-wide JS exists:
  - keep it minimal
  - it must be justified + logged

## 3) CLS Budget (Qualitative)
- No visible CLS in:
  - hero
  - product gallery
  - cart drawer
If CLS is visible, it is a fail.

## 4) Asset Budgets (Qualitative)
- Prefer component-scoped CSS/JS over global assets.
- `critical.css` contains tokens and primitives only.

## 5) Accessibility Budget
- No interactive component ships without keyboard support and focus behavior.

END

