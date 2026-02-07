/docs/COMPATIBILITY.md
# COMPATIBILITY — Tested Apps, Known Conflicts, and Integration Notes
Version: 0.1  
Purpose: Provide a clear, honest compatibility matrix for buyers and for internal QA.  
Rule: Do not promise universal compatibility. Only list what is tested.

## 0) Policy
- “Compatible” means: core UX does not break and the app’s UI is acceptable in RTL.
- “Partially compatible” means: works, but needs CSS tweaks or has RTL quirks.
- “Conflict” means: causes layout/JS issues or RTL breaks; not recommended without custom work.

## 1) Test Method (Standard)
For each app tested:
- Test locale: Hebrew (RTL) primary, English (LTR) secondary
- Templates tested: Home, Collection, Product, Cart, Search
- Devices: iOS Safari + Android Chrome + Desktop Chrome
- Flows:
  - Purchase loop (Home → Collection → PDP → Cart)
  - Cart drawer open/close and quantity edits
  - Search results and no-results recovery

Record results using the template in §5.

## 2) App Categories We Care About (Israel SMB Reality)
- Reviews (social proof)
- Upsell / bundles
- Currency / payments messaging (installments)
- Email/SMS (does not affect storefront UI heavily)
- Shipping / delivery widgets
- Size charts (apparel)
- WhatsApp widgets

## 3) Compatibility Status Codes
- ✅ Compatible
- ⚠️ Partially Compatible
- ❌ Conflict
- ⏳ Not Tested

## 4) Known Risk Areas (Common Conflict Zones)
These are the typical reasons an app breaks RTL themes:
- App injects LTR-only CSS (left/right positioning, fixed offsets)
- App’s widget assumes English word lengths
- App’s modal/drawer conflicts with theme drawer (z-index/focus trap)
- App overrides global typography or button styles
- App scripts run site-wide and impact performance/CLS

If an app hits one of these, mark ⚠️ or ❌ and document mitigation.

## 5) Entry Template (Copy/Paste)
### <APP NAME> — <CATEGORY>
**Status:** ✅ / ⚠️ / ❌ / ⏳  
**Test Date:** YYYY-MM-DD  
**Version/Plan:** (if known)  
**Pages Tested:** Home / Collection / Product / Cart / Search  
**Devices Tested:** iOS Safari / Android Chrome / Desktop Chrome  
**Result Summary:** 2–4 lines.  
**RTL Notes:**
- Alignment:
- Icon direction:
- Mixed text (numbers/URL/email):
- Modal/drawer behavior:
**Performance Notes:**
- Added scripts site-wide? (yes/no)
- CLS introduced? (yes/no)
**Mitigation (if ⚠️):**
- CSS patch location:
- Settings toggles:
**Recommendation to Buyer:**
- Use as-is / Use with minor tweak / Avoid

## 6) Current Matrix (Start Empty Until Tested)
> Populate only after real tests. Do not guess.

### Reviews
- Judge.me — ⏳ Not Tested
- Loox — ⏳ Not Tested
- Yotpo — ⏳ Not Tested
- Shopify Product Reviews — ⏳ Not Tested

### Upsell / Bundles
- Rebuy — ⏳ Not Tested
- Frequently Bought Together — ⏳ Not Tested
- Bundler — ⏳ Not Tested

### Shipping / Delivery Widgets
- ParcelPanel — ⏳ Not Tested
- AfterShip — ⏳ Not Tested

### Size Charts
- Kiwi Size Chart — ⏳ Not Tested

### WhatsApp Widgets
- (Generic WhatsApp chat widgets) — ⏳ Not Tested

## 7) Theme-Native Alternatives (Preferred)
Where possible, prefer theme-native features to reduce dependency:
- Trust blocks (native)
- Testimonials/UGC (native)
- Gift mode (native)
- WhatsApp conversion bar (native)

END

