/docs/RELEASE_CHECKLIST.md
# RELEASE_CHECKLIST — RC + Theme Store Readiness
Version: 0.1  
Goal: Make releases repeatable and submission-safe.

## 1) Code Freeze Conditions
- No open failing items in Regression Checklist.
- No known fatal issues in core flows.

## 2) QA
- Run full `03_QA_TEST_MATRIX.md` in Hebrew RTL.
- Run minimal LTR smoke: home, collection, PDP, cart.
- Verify no CLS in hero/gallery/cart drawer.

## 3) Localization
- Confirm no missing keys (storefront + schema).
- Confirm Hebrew editor UI labels look coherent.
- Confirm canonical terminology (07) used consistently.

## 4) Documentation Completeness
- README_FOR_IDE updated
- Section Inventory accurate (05)
- Theme Styles spec matches implementation (08)
- Compatibility entries reflect only tested apps
- Support policy matches offer

## 5) Decision Log + Versioning
- Add release entry in `04_CHANGELOG_DECISIONS.md`.
- Confirm version bump policy applied.

## 6) Packaging / Delivery
- Ensure canonical theme folder is correct.
- Ensure no stray experimental folders included.
- Confirm backups exist (git tag + zip + Shopify duplicate if relevant).

## 7) Final Smoke
- Run REGRESSION_CHECKLIST.md on dev theme
- Confirm console clean

END

