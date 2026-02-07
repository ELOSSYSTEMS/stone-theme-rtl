/docs/REGRESSION_CHECKLIST.md
# REGRESSION_CHECKLIST — Fast Checks After Any Change (10–15 Minutes)
Version: 0.1  
Goal: Catch breakage without running full QA matrix every time.

## 1) Pages (Hebrew RTL)
1) Home loads, no broken sections
2) Collection loads, grid visible
3) Product loads, gallery stable
4) Cart drawer opens/closes
5) Cart page loads
6) Checkout CTA visible

## 2) Interactions
7) Add to cart works
8) Quantity change works
9) Remove item works
10) Search opens/works (basic)

## 3) RTL/Bidi Sanity
11) Icon direction correct for chevrons/arrows
12) Coupon/email/URL test string doesn’t reorder badly (use 09 suite)

## 4) A11y Smoke
13) Tab through header controls
14) Drawer closes with Escape and returns focus

## 5) Console
15) No fatal JS errors

If any item fails → rollback protocol applies for risky batches.

END

