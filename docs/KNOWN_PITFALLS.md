/docs/KNOWN_PITFALLS.md
# KNOWN_PITFALLS — Accumulated Gotchas (Prevent Repeat Pain)
Version: 0.1  
Rule: Add items here when discovered. Keep it practical.

## 1) JSON Template Breakers
- Referencing a section type that doesn’t exist breaks editor load.
- Renaming section types is high-risk and often not worth it.

## 2) Schema Limits
- Shopify section block count limits can trigger save errors.
- Keep blocks conservative; prefer select settings for variants.

## 3) Bidi Traps
- Email/URL/SKU/coupon strings in RTL must be isolated with `dir="ltr"` and `unicode-bidi: isolate`.
- Hyphens reorder in RTL unless isolated.

## 4) Drawer Conflicts
- z-index and focus trap bugs are common.
- Ensure only one focus trap is active at a time.

## 5) CLS Traps
- Hero and gallery without reserved aspect ratio cause visible shift.
- Lazy-loading above-the-fold images can cause shift if not reserved.

## 6) Hardcoded Strings
- Hardcoded Hebrew in Liquid/schema causes future localization pain.
- Always use `t:` keys.

## 7) Global CSS Collisions
- Broad selectors create invisible regressions.
- Keep selectors scoped to component root classes.

END

