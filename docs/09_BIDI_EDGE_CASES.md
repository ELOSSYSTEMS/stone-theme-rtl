/docs/09_BIDI_EDGE_CASES.md
# 09_BIDI_EDGE_CASES — RTL/Bidi Engineering Playbook (Deep)
Version: 0.1  
Goal: Prevent subtle RTL bugs in Hebrew + mixed LTR segments.

## 0) Core Principle
In RTL UI, mixed-direction strings must be isolated to avoid reordering.
Use LTR islands for strictly LTR content; use isolation for mixed.

## 1) Common Failure Modes
1) Email in RTL sentence breaks order: `test@example.com`
2) URL wraps and reorders punctuation
3) SKU `ABC-123` shows as `123-ABC`
4) Coupon code displays with reversed characters
5) Phone numbers split incorrectly
6) Currency symbol position inconsistent
7) Mixed Hebrew + “XL” or “iPhone” becomes visually scrambled

## 2) Mandatory LTR Islands (Wrap These)
Wrap with `dir="ltr"` and bidi isolation:
- email
- URLs
- SKU
- coupon codes
- phone numbers (often best)
- tracking numbers

Pattern:
- HTML: `<span dir="ltr" class="bidi-ltr">...</span>`
- CSS: `.bidi-ltr { unicode-bidi: isolate; }`

## 3) Mixed Text Islands (Hebrew sentence containing numbers/Latin)
Use `unicode-bidi: plaintext` cautiously when:
- You have unpredictable mixed segments, especially user-generated.

Pattern:
- `.bidi-plain { unicode-bidi: plaintext; }`

## 4) Inputs Direction Rules
- Email input: `dir="ltr"`
- Coupon input: `dir="ltr"`
- Phone input: `dir="ltr"` (unless merchant wants RTL formatting)
- Quantity input: can remain RTL but must display numbers normally

Ensure placeholders do not look reversed.

## 5) Punctuation and Separators
- Hyphens in SKUs should remain LTR.
- Colons in Hebrew labels (e.g., “קוד: SAVE10”) often render fine but must be tested.

## 6) Carousel/Slider Direction
Rules:
- Swipe direction must feel natural in RTL:
  - “Next” is visually left or right depending on convention—define consistently and test.
- Arrows must mirror.
- Pagination dots must read right-to-left in ordering.

## 7) Tests (Must Use)
Use the string suite:
- “מידה: XL”
- “דגם ABC-123”
- “קוד קופון: SAVE10”
- “מייל: test@example.com”
- “קישור: https://example.com/path?x=1”
- “טלפון: 052-123-4567”

These must pass in:
- Header (contact)
- PDP (details)
- Cart (coupon)
- Footer (email)

## 8) Regression Prevention
If a bidi fix is added:
- Add a QA note referencing 03_QA_TEST_MATRIX edge checks.
- Update any helper snippet or CSS utility in one place (no local hacks).

END

