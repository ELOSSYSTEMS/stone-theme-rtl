/docs/06_DESIGN_TOKENS.md
# 06_DESIGN_TOKENS — Design System & Premium Rhythm (Authoritative)
Version: 0.1  
Rule: All sections must use these tokens/variables and avoid ad-hoc styling.

## 0) Philosophy
- Premium in Hebrew = generous spacing, restrained type, predictable rhythm.
- Consistency beats “more options.”
- Defaults must look premium without configuration.

## 1) Token Source of Truth
- Primary: CSS custom properties in `assets/critical.css`
- Sections may introduce local CSS vars only for component-specific needs.

## 2) Spacing Scale (CSS Vars)
Define in `:root` as:
- `--space-0: 0`
- `--space-1: 4px`
- `--space-2: 8px`
- `--space-3: 12px`
- `--space-4: 16px`
- `--space-5: 20px`
- `--space-6: 24px`
- `--space-7: 32px`
- `--space-8: 40px`
- `--space-9: 48px`
- `--space-10: 64px`

Rules:
- Section vertical padding must be from {7,8,9,10} by default.
- Internal element gaps should be {3–6}.

## 3) Container Widths
Define utility classes or vars:
- `--page-max: 1200px` (desktop max)
- `--page-pad: 16px` (mobile), 24px (tablet), 32px (desktop)
Rules:
- All sections align to the same container system.
- Full-bleed media must still preserve internal padding.

## 4) Typography Scale (Hebrew-first)
Define:
- Base font size: 16px
- Line height (Hebrew-friendly):
  - body: 1.55–1.75
  - headings: 1.1–1.25
Rules:
- Avoid overly tight tracking in Hebrew.
- Avoid extremely thin weights for Hebrew body text.

Suggested sizes:
- `--font-size-xs: 12px`
- `--font-size-sm: 14px`
- `--font-size-md: 16px`
- `--font-size-lg: 18px`
- `--font-size-xl: 22px`
- `--font-size-2xl: 28px`
- `--font-size-3xl: 36px`

## 5) Font Roles
Theme settings should expose:
- Body font
- Heading font
- Accent font (optional)

Rules:
- If only 2 fonts: use same for body+heading with weight differences.
- Numerals must remain legible in Hebrew paragraphs.

## 6) Radius / Borders / Shadows
- `--radius-sm: 8px`
- `--radius-md: 12px`
- `--radius-lg: 16px`

Borders:
- `--border-1: 1px solid var(--color-border)`

Shadows (restrained):
- `--shadow-1: 0 1px 2px rgba(0,0,0,0.06)`
- `--shadow-2: 0 4px 16px rgba(0,0,0,0.08)`

Rules:
- Use shadow sparingly; prefer whitespace.
- Buttons: no heavy shadows by default.

## 7) Buttons (Canonical Styles)
Variants:
- Primary
- Secondary
- Ghost (text button)
Rules:
- Minimum height mobile: 44px
- Padding uses logical properties (inline start/end)
- Focus ring always visible
- Disabled state distinct

## 8) Forms (Canonical)
- Inputs height: 44px
- Clear error states (border + text)
- Use logical properties for padding
- For email/phone/coupon inputs inside RTL, consider `dir="ltr"` at field level.

## 9) Iconography Rules (Directional)
- Directional icons must mirror in RTL.
- Non-directional icons must not mirror.

Implementation guidance:
- Use a wrapper class `.icon--dir` for mirrorable icons.
- Apply:
  - `html[dir="rtl"] .icon--dir { transform: scaleX(-1); }`

## 10) Section Rhythm Rules (Premium Defaults)
Default section padding:
- Top/bottom: `--space-9` on desktop, `--space-8` on mobile.

Text blocks:
- Heading to paragraph gap: `--space-4`
- Paragraph to CTA gap: `--space-5`

Grids:
- Grid gap default: `--space-6`

## 11) Color System (Tokenized)
Expose minimal scheme tokens:
- Background
- Text
- Muted text
- Border
- Accent
Rules:
- Avoid too many schemes; 2–3 max to keep coherence.

## 12) Do Not Do (Hard Style Anti-Patterns)
- Random per-section padding not tied to scale
- Mixed border radii without token
- LTR-only padding/positioning
- Too many typography variants (creates incoherence)

END

