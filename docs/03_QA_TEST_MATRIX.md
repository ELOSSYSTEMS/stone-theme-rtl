/docs/03_QA_TEST_MATRIX.md
# 03_QA_TEST_MATRIX — RTL/Hebrew Theme QA Gates (Objective Tests)
Version: 0.1  
Rule: Any change must reference the relevant tests below and confirm pass/fail.

## 0) Environments
Minimum devices/browsers:
- iOS Safari (mobile)
- Android Chrome (mobile)
- Desktop Chrome (latest)
- Desktop Safari or Firefox (optional but recommended)

Locales:
- Hebrew (RTL) — PRIMARY
- English (LTR) — SECONDARY (must not break)

## 1) Core User Flows (Must Pass)
### Flow A — Purchase Loop
1) Home → open menu → navigate to collection
2) Collection → sort → filter → open product
3) Product → change variant → add to cart
4) Cart drawer → adjust quantity → go to cart page
5) Cart page → proceed to checkout (checkout UI not tested for RTL theme control, but transition must work)

Pass criteria:
- No broken RTL alignment
- Icons direction correct
- No missing translations
- No unusable controls on mobile

### Flow B — Search Loop
1) Open search from header
2) Search for common query → open product
3) Search for nonsense query → see no-results recovery content → click suggestion

Pass criteria:
- RTL text highlighting doesn’t scramble
- No-results is helpful and translated

### Flow C — Navigation Depth
1) Open mobile drawer
2) Enter submenu
3) Use back navigation
4) Close drawer by:
   - X button
   - tapping overlay
   - Escape key (desktop)
5) Confirm focus returns to trigger

Pass criteria:
- Back arrows and transitions are RTL-correct
- Focus management correct

## 2) RTL/Bidi Edge Cases (Must Pass)
### 2.1 Mixed Text Rendering
Test strings in Hebrew UI contexts:
- “מידה: XL”
- “דגם ABC-123”
- “קוד קופון: SAVE10”
- “מייל: test@example.com”
- “קישור: https://example.com/path?x=1”

Pass criteria:
- LTR segments render left-to-right inside RTL without character scrambling
- Line breaks do not reorder characters
- Cursor in inputs behaves predictably

### 2.2 Numeric Formatting
- Prices with thousands separators
- Compare-at prices
- Percent discounts
- Quantity stepper values

Pass criteria:
- Numbers not reversed
- Currency symbol placement consistent

### 2.3 Directional UI
Verify in RTL:
- Breadcrumb arrows
- Pagination arrows
- Carousel arrows
- Accordion chevrons
- “Back” buttons in drawers/modals

Pass criteria:
- All directional icons point the correct way in RTL
- Interactions match visual direction

## 3) Accessibility Gates (Must Pass)
### 3.1 Keyboard Navigation
- Tab through header controls
- Open drawer with keyboard
- Navigate within drawer
- Close drawer with Escape
- Tab through PDP buy box controls
- Operate accordion with keyboard

Pass criteria:
- Visible focus ring always present
- Focus order logical in RTL
- No focus trapped unintentionally

### 3.2 ARIA + Labels
- Buttons have accessible names
- Inputs have labels or aria-labels
- Drawer has role and state attributes

Pass criteria:
- Screen-reader friendly structure (baseline)

### 3.3 Contrast + Motion
- Default theme style meets readable contrast
- Motion is subtle; respect reduced motion if implemented

Pass criteria:
- No unreadable default states

## 4) Performance Gates (Must Pass)
### 4.1 CLS Hotspots
Check:
- Hero loads without shifting
- Product gallery reserves space
- Cart drawer open doesn’t reflow page

Pass criteria:
- No visible jump on load/interaction

### 4.2 Asset Scope
- Component CSS/JS loaded only where used
- `critical.css` minimal

Pass criteria:
- No large unused scripts on all pages

## 5) Regression Checklist (Run Before Any Push)
- Header/menu/drawer: RTL & keyboard pass
- Collection filters: mobile usability pass
- Product page: variants + sticky CTA pass
- Cart drawer: quantity/remove/close pass
- No missing translations (he + schema)
- Icon directions pass in RTL

## 6) Recording Results
Every change must add a short QA note in the commit/PR description:
- Locale tested: HE / EN
- Devices tested: iOS / Android / Desktop
- Flows passed: A/B/C
- Edge cases checked: 2.1/2.2/2.3
- Any known issues logged in 04_CHANGELOG_DECISIONS.md

END

