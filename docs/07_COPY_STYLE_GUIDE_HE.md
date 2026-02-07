/docs/07_COPY_STYLE_GUIDE_HE.md
# 07_COPY_STYLE_GUIDE_HE — Hebrew Microcopy & Tone Governance
Version: 0.1  
Goal: Ensure every UI string in Hebrew is coherent, premium, and conversion-safe.

## 0) Tone Target
Neutral, confident, premium, concise.
No slang by default. No hype. No manipulation.

## 1) Core Principles
- Short sentences. Direct verbs.
- Prefer clarity over cleverness.
- Avoid excessive punctuation.
- Avoid English where Hebrew is standard.

## 2) Canonical Terminology (UI)
Use consistent labels across the theme. Do not invent synonyms per section.

### Navigation
- Menu: "תפריט"
- Search: "חיפוש"
- Account: "חשבון"
- Cart: "עגלה"

### Commerce
- Add to cart: "הוספה לעגלה"
- Sold out: "אזל מהמלאי"
- Sale: "מבצע"
- New: "חדש"
- Compare at: "במקום"
- Quantity: "כמות"
- Size: "מידה"
- Color: "צבע"
- Details: "פרטים"
- Delivery: "משלוח"
- Returns: "החזרות"
- Warranty: "אחריות"

### System States
- Loading: "טוען…"
- Error: "שגיאה"
- No results: "לא נמצאו תוצאות"

## 3) Error Message Style
Rules:
- State what happened + what to do next.
- No blame.
Templates:
- “לא הצלחנו לעדכן את העגלה. נסו שוב.”
- “בחרו מידה כדי להמשיך.”
- “שדה חובה.”

## 4) Empty States
Cart empty:
- Title: “העגלה ריקה”
- CTA: “חזרה לקנייה”
- Optional subtext: “אפשר להוסיף פריטים ולהמשיך לתשלום.”

Search empty:
- Title: “לא נמצאו תוצאות”
- Suggestions: “נסו מילה אחרת או עברו לקטגוריות.”

## 5) Trust Copy (Israel-appropriate)
Trust lines should be short and factual.
Examples (generic, editable):
- “תשלום מאובטח”
- “שירות בוואטסאפ”
- “מדיניות החזרות ברורה”
- “אחריות לפי תנאי האתר”

Avoid:
- “הכי טוב בישראל”
- “הבטחה מטורפת”
- “100% מושלם”

## 6) WhatsApp Copy (If enabled)
Guidelines:
- Always include a question framing.
- Avoid demanding language.
Examples:
- “רוצים להתייעץ? כתבו לנו בוואטסאפ”
- “שאלה על מידה או מלאי? דברו איתנו”

## 7) Translation Key Governance
- Keys must map to these exact Hebrew strings unless intentionally changed.
- Any change to canonical phrases must be logged in 04_CHANGELOG_DECISIONS.md.

## 8) Banned Phrases (UI)
Avoid:
- “דחוף”
- “חייבים”
- “אל תפספסו” (unless merchant explicitly chooses a promo tone pack later)
- Excessive emojis in UI (allowed in marketing content sections only, not system UI)

## 9) Punctuation & Typography
- Use “…” sparingly.
- Use Hebrew quotes properly where possible.
- Keep numeric formatting consistent.

END

