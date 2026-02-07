/docs/05_SECTION_INVENTORY.md
# 05_SECTION_INVENTORY — Shipped Components Registry (Single Source of Truth)
Version: 0.1  
Rule: This file enumerates every shipped component.  
Rule: No new section/block/snippet may be added without updating this file.

## 0) How to Use
- Before building anything, check if it already exists here.
- Each entry must include: purpose, placement, settings, i18n keys, RTL notes, assets, QA tests.
- This file is “scope reality.” If it’s not listed, it’s not part of the product.

## 1) Status Codes
- PLANNED: approved, not implemented
- IN_PROGRESS: partially implemented
- SHIPPED: implemented + QA passed
- DEPRECATED: replaced; must not be used in templates

## 2) Inventory Table (Populate as You Build)
> Start with PLANNED entries. Move to SHIPPED only after QA.

### 2.1 Global Shell
#### Header
- **ID:** SEC.HEADER.001
- **Type:** Section
- **Status:** PLANNED
- **File:** `sections/header.liquid`
- **Purpose:** Site header with RTL navigation, drawer, search entry, cart entry.
- **Used in templates:** global (layout)
- **Key settings (groups):**
  - Layout: logo position, menu assignment, alignment
  - Behavior: sticky, drawer animation
  - Elements: search toggle, account toggle, cart count
- **i18n namespaces:** `header.*`, `nav.*`, `a11y.*`
- **RTL notes:** drawer side, submenu back behavior, chevron mirroring
- **Assets:** component CSS/JS only
- **QA:** 03_QA_TEST_MATRIX Flow A/C + Edge 2.3 + A11y 3.1

#### Footer
- **ID:** SEC.FOOTER.001
- **Type:** Section
- **Status:** PLANNED
- **File:** `sections/footer.liquid`
- **Purpose:** Multi-column footer with menus + trust row + optional newsletter.
- **Used in templates:** global (layout)
- **i18n namespaces:** `footer.*`, `trust.*`, `newsletter.*`
- **RTL notes:** columns order RTL, link alignment, LTR islands for email/URL
- **QA:** Flow A + Edge 2.1 + A11y 3.1

### 2.2 Home Sections
#### Hero (Image/Video)
- **ID:** SEC.HOME.HERO.001
- **Type:** Section
- **Status:** PLANNED
- **File:** `sections/home-hero.liquid`
- **Purpose:** Premium hero with image and optional video.
- **Templates:** `templates/index.json`
- **Settings:** media, heading/subheading, CTA, layout variant, height, overlay
- **i18n:** `home.hero.*`
- **RTL notes:** text alignment start/end, CTA placement logical
- **Perf notes:** reserve space; lazy-load non-critical media
- **QA:** Perf 4.1 + RTL Edge 2.3

#### Featured Collections
- **ID:** SEC.HOME.COLLECTIONS.001
- **Type:** Section
- **Status:** PLANNED
- **File:** `sections/home-featured-collections.liquid`
- **Purpose:** Collection list/grid with category-first merchandising.
- **i18n:** `home.collections.*`
- **QA:** Flow A

#### Featured Products
- **ID:** SEC.HOME.PRODUCTS.001
- **Type:** Section
- **Status:** PLANNED
- **File:** `sections/home-featured-products.liquid`
- **Purpose:** Showcase products with product-card.
- **Dependencies:** `snippets/product-card.liquid`
- **i18n:** `home.products.*`

#### Editorial Image-with-Text
- **ID:** SEC.HOME.EDITORIAL.001
- **Type:** Section
- **Status:** PLANNED
- **File:** `sections/home-editorial.liquid`
- **Purpose:** Premium storytelling; variants (left/right media).
- **i18n:** `home.editorial.*`

#### UGC / Gallery
- **ID:** SEC.HOME.UGC.001
- **Type:** Section
- **Status:** PLANNED
- **File:** `sections/home-ugc-gallery.liquid`
- **Purpose:** RTL-safe gallery/rail for UGC + quotes.
- **i18n:** `ugc.*`
- **RTL notes:** swipe direction, arrow mirroring
- **Perf notes:** lazy-load images; avoid heavy slider libs

#### Testimonials
- **ID:** SEC.HOME.TESTIMONIALS.001
- **Type:** Section
- **Status:** PLANNED
- **File:** `sections/home-testimonials.liquid`
- **Purpose:** Social proof slider/list.
- **i18n:** `testimonials.*`

#### Brand Manifesto / Rich Text
- **ID:** SEC.HOME.MANIFESTO.001
- **Type:** Section
- **Status:** PLANNED
- **File:** `sections/home-manifesto.liquid`
- **Purpose:** Brand voice block.
- **i18n:** `manifesto.*`

#### Trust Strip
- **ID:** SEC.HOME.TRUST.001
- **Type:** Section
- **Status:** PLANNED
- **File:** `sections/trust-strip.liquid`
- **Purpose:** Icons + short trust lines.
- **i18n:** `trust.*`

### 2.3 Collection
#### Collection Banner
- **ID:** SEC.COLLECTION.BANNER.001
- **Type:** Section
- **Status:** PLANNED
- **File:** `sections/collection-banner.liquid`

#### Collection Grid + Filters
- **ID:** SEC.COLLECTION.GRID.001
- **Type:** Section
- **Status:** PLANNED
- **File:** `sections/collection-grid.liquid`
- **Purpose:** Grid with sort + filters.
- **RTL notes:** filter drawer side, close/back UX
- **Perf notes:** keep JS minimal

### 2.4 Product
#### Product Media Gallery
- **ID:** SEC.PRODUCT.GALLERY.001
- **Type:** Section or Block
- **Status:** PLANNED
- **File:** `sections/product-main.liquid` (or `blocks/product-gallery.liquid`)
- **Purpose:** Media carousel + thumbnails.
- **Perf:** reserve aspect ratio; avoid CLS

#### Product Buy Box
- **ID:** SEC.PRODUCT.BUYBOX.001
- **Status:** PLANNED
- **Purpose:** Variants, quantity, sticky CTA.
- **RTL notes:** sticky bar direction, icon mirroring

#### Product Accordion
- **ID:** SEC.PRODUCT.ACCORDION.001
- **Status:** PLANNED
- **Purpose:** Details/shipping/returns/warranty in Hebrew.

#### Complementary Products
- **ID:** SEC.PRODUCT.UPSELL.001
- **Status:** PLANNED

### 2.5 Cart
#### Cart Drawer
- **ID:** SEC.CART.DRAWER.001
- **Status:** PLANNED
- **Purpose:** Mini cart with focus trap, quantity edits, upsell slot.
- **RTL notes:** drawer side, back/close logic
- **A11y:** focus trapping required

#### Cart Main
- **ID:** SEC.CART.MAIN.001
- **Status:** PLANNED

### 2.6 Utility
#### FAQ
- **ID:** SEC.UTIL.FAQ.001
- **Status:** PLANNED

#### Contact (Phone/WhatsApp)
- **ID:** SEC.UTIL.CONTACT.001
- **Status:** PLANNED

### 2.7 Core Snippets / Blocks
#### Product Card
- **ID:** SNP.PRODUCT.CARD.001
- **Type:** Snippet or Block
- **Status:** PLANNED
- **File:** `snippets/product-card.liquid`
- **Purpose:** Reusable product tile with badges/pricing.
- **RTL notes:** price + compare alignment, badge placement logical

#### Icon System
- **ID:** SNP.ICON.001
- **Status:** PLANNED
- **Files:** `snippets/icon-*.liquid`

#### Bidi Utilities
- **ID:** SNP.BIDI.001
- **Status:** PLANNED
- **Purpose:** Wrapper helpers for LTR islands.

### 2.8 Israel Differentiators (Novel)
#### WhatsApp Conversion Bar
- **ID:** SEC.ISR.WA.001
- **Status:** PLANNED

#### Delivery Promise Block
- **ID:** SEC.ISR.DELIVERY.001
- **Status:** PLANNED

#### Trust Stack Builder
- **ID:** SEC.ISR.TRUSTSTACK.001
- **Status:** PLANNED

#### Gift Mode
- **ID:** SEC.ISR.GIFT.001
- **Status:** PLANNED

#### Holiday Moment Banner
- **ID:** SEC.ISR.HOLIDAY.001
- **Status:** PLANNED

END

