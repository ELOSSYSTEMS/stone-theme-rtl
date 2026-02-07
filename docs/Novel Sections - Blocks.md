# Novel Sections / Blocks — RTL Hebrew-First Theme (Israel SMB Differentiators)
Goal: Propose unique, high-appeal, low-friction sections/blocks that make Israeli SMBs choose this theme over generic themes.  
Constraints: Theme Store quality, RTL-native, minimal app dependency, minimal required metafields, performant, accessible, mobile-first.

---

## 1) WhatsApp Conversion Bar (Smart CTA)
**Concept:** A configurable sticky WhatsApp bar that adapts by page type and user intent.  
**Why Israel:** WhatsApp is a primary commerce channel; many SMBs close sales in chat.  
**Unique Angle:** Not just an icon—smart placement + messaging presets:
- PDP: “שאלה על מידה/מלאי?” / “שלחו תמונה ונעזור”
- Cart: “רוצים לוודא לפני תשלום?”
- Collection: “צריך המלצה מהירה?”
**Settings:** enable per template, text presets, phone, UTM parameters, business hours, fallback message.  
**Implementation:** Section + small JS; no apps.  
**Risk:** Must remain non-intrusive; include disable on checkout.

---

## 2) Delivery Promise Block (Israel Logistics Truth)
**Concept:** A “Delivery Promise” block that shows delivery method + ETA messaging and pickup options, scoped by region.  
**Why Israel:** Delivery expectations differ by area; trust improves conversions.  
**Unique Angle:** Uses simple “region groups” configured in Theme Editor (not dynamic carrier rates):
- Gush Dan / Sharon / North / South presets
- “Delivery days” and cutoff times
**Settings:** region labels, message per region, icons, show on PDP/cart/footer.  
**Implementation:** Block rendered via settings + optional customer geolocation toggle (off by default).

---

## 3) Hebrew Microcopy Pack (Tone Switcher)
**Concept:** A “Tone pack” control that changes microcopy style across key UI strings.  
**Why Israel:** Different SMBs want different voice (formal, friendly, luxury, direct).  
**Unique Angle:** Switches translation dictionaries (or key namespaces) without rewriting theme code:
- “נקי ורשמי”
- “חם ואישי”
- “יוקרתי ושקט”
**Settings:** tone selector; applies to cart/search/buttons/errors.  
**Implementation:** Locale key namespace routing (e.g., `ui.tone_1.*`).  
**Risk:** Must be carefully authored; prevents merchants from writing inconsistent UI.

---

## 4) “Installments / תשלומים” Messaging Block
**Concept:** A block that displays installment messaging and “pay in X” copy (static or provider-linked if available).  
**Why Israel:** Installments are common and expected; raises AOV.  
**Unique Angle:** Configurable display logic:
- Show above ₪X
- Show only on PDP/cart
- Different copy per product type
**Settings:** threshold, number of payments, provider name (manual), disclaimer.  
**Implementation:** Pure Liquid settings + price checks; no payments integration required.

---

## 5) Trust Stack Builder (Israel Proof Pattern)
**Concept:** A modular trust section with a builder UI: badges + short lines + optional “expand for details.”  
**Why Israel:** Buyers need reassurance fast; “scam anxiety” is real.  
**Unique Angle:** Prebuilt Israeli-relevant trust items:
- “אחריות”
- “החלפה/החזר”
- “תשלום מאובטח”
- “שירות בוואטסאפ”
- “משלוח מהיר בישראל”
**Settings:** reorderable blocks, icons, short/long text, show near CTA and cart totals.  
**Implementation:** Section with blocks; accordion expansion.

---

## 6) FAQ That Reduces Support Tickets (Smart FAQ)
**Concept:** FAQ section that supports “FAQ by template” and “FAQ by collection” without metafields.  
**Why Israel:** SMBs drown in repeated WhatsApp questions.  
**Unique Angle:** Built-in “Top 5 questions” presets per vertical:
- Apparel: sizes/returns/shipping
- Beauty: ingredients/usage/sensitivity
- Home: materials/care/assembly
**Settings:** choose preset pack + manual overrides; show in PDP or dedicated FAQ page.  
**Implementation:** Schema blocks + conditional rendering per template.

---

## 7) Social Proof Rail (UGC + Reviews Hybrid)
**Concept:** A horizontal “proof rail” that mixes UGC images + short testimonials + optional rating snippet.  
**Why Israel:** Social proof drives trust; many SMBs lack full reviews apps.  
**Unique Angle:** Accepts:
- images uploaded in theme editor
- short quote + first name + city
- optional star rating (manual)
**Settings:** rail density, autoplay on/off, RTL swipe behavior, fallback layout.  
**Implementation:** Lightweight slider with RTL-safe arrows.

---

## 8) “Before You Buy” Checklist (Conversion Anxiety Reducer)
**Concept:** A checklist block near PDP CTA: “מה חשוב לדעת לפני שמזמינים” with expandable details.  
**Why Israel:** Reduces buyer uncertainty; fewer pre-purchase messages.  
**Unique Angle:** Vertical-specific checklist presets:
- Apparel: size/fit, fabric, returns
- Beauty: usage, skin type, storage
- Home: dimensions, materials, care, assembly
**Settings:** preset selection + editable items.  
**Implementation:** Block + accordion.

---

## 9) Hebrew-First Size & Fit Module (Apparel Differentiator)
**Concept:** A built-in size guide section with easy table + “how to measure” steps and image slot.  
**Why Israel:** Size confusion is high friction; reduces returns.  
**Unique Angle:** Supports:
- “Israel sizing” guidance (S/M/L mapping, cm focus)
- Optional “model info” block (height/wearing size)  
**Settings:** table rows, measurement labels, notes, show per product template (not metafield-heavy).  
**Implementation:** Section + settings; optionally allow per-template customization.

---

## 10) “Gift Mode” Switch (Israel Gift Culture)
**Concept:** A block that enables gift UX without an app:
- Gift note
- “Send without invoice” copy
- Gift wrap toggle (manual product add-on or line item property)
**Why Israel:** Gifts are frequent (holidays, birthdays, host gifts).  
**Unique Angle:** Works in cart drawer + cart page; integrates via line item properties.  
**Settings:** enable gift wrap, label text, add-on product handle (optional), note character limit.  
**Implementation:** Minimal JS + cart attributes.

---

## 11) Holiday Moment Banner (Israel Calendar Engine)
**Concept:** A banner/section that supports Israel holiday presets (Rosh Hashanah, Passover, Shavuot, etc.) with scheduling.  
**Why Israel:** Seasonal spikes; SMBs want quick swapping without redesign.  
**Unique Angle:** “Schedule” with start/end dates set in theme editor:
- show banner automatically during date window
- fallback banner off-season
**Settings:** date windows (manual), message, CTA, template targeting.  
**Implementation:** Theme settings store dates; Liquid compares to `now` (store timezone considerations).

---

## 12) “Phone-First” Contact Drawer (Service Differentiator)
**Concept:** A contact drawer with 3 actions: WhatsApp, Call, Email—RTL-native, accessible, branded.  
**Why Israel:** Many SMB buyers want instant human response.  
**Unique Angle:** Shows business hours + “response time” promise + quick topic buttons (size, delivery, warranty).  
**Settings:** numbers, hours, topics, auto-message templates.  
**Implementation:** Section/snippet + minimal JS.

---

## 13) “Compare Variants” Mini Table (High-AOV Aid)
**Concept:** A block that renders a simple comparison table for variants (size/finish/material) without metafields.  
**Why Israel:** Helps decision; reduces WhatsApp questions; increases upsell.  
**Unique Angle:** Merchant defines rows in editor once per product template.  
**Settings:** columns, row labels, highlight recommended variant.  
**Implementation:** Block with editor-defined table.

---

## 14) “Proof of Local” Badge System (Made-in-Israel / Local)
**Concept:** A badge system that highlights local production, pickup location, kosher (if relevant), warranty, etc.  
**Why Israel:** Local trust and shipping confidence matter.  
**Unique Angle:** Badge pack per store type; badge display rules by product tag (optional).  
**Settings:** badges, mapping rules, placement on cards/PDP.  
**Implementation:** Liquid tag checks + schema config; no apps.

---

# Shortlist: Top 10 to Build First (Highest ROI)
1) WhatsApp Conversion Bar (Smart CTA)  
2) Trust Stack Builder  
3) Delivery Promise Block (region messaging)  
4) Gift Mode Switch  
5) Holiday Moment Banner (scheduler)  
6) Social Proof Rail (UGC + testimonials)  
7) “Before You Buy” Checklist  
8) Hebrew Microcopy Pack (tone switcher)  
9) Size & Fit Module  
10) Phone-First Contact Drawer  

---

## Implementation Notes (Theme Store Safe)
- Avoid anything that claims real-time carrier ETAs unless you integrate Shopify-native capabilities carefully.
- Keep defaults conservative; allow full disable.
- Ensure every section/block:
  - is RTL/LTR safe
  - has Hebrew schema labels
  - ships with accessible markup and keyboard support
  - does not bloat `critical.css`

END

