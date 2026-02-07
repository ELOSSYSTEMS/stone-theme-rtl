# Checkout Extensibility Notes (WMW Public Material)

Primary article:
- “A Closer Look: HyperX's Migration to Shopify Checkout Extensibility”
  https://www.wemakewebsites.com/blog/a-closer-look-hyperx-shopify-checkout-extensibility

## Key migration framing
- Verified: They contrast checkout.liquid customization (rigid; “hacky” workarounds) with Checkout Extensibility.
  Source: https://www.wemakewebsites.com/blog/a-closer-look-hyperx-shopify-checkout-extensibility
- Verified: They describe extension primitives: Checkout UI extensions, Shopify Functions, Checkout Branding API, Web Pixels.
  Source: https://www.wemakewebsites.com/blog/a-closer-look-hyperx-shopify-checkout-extensibility

## Practical patterns mentioned
- Verified: Upsells/cross-sells via a checkout UI extension (pre-purchase product offer).
- Verified: Bundles using Shopify’s Bundles app (noted as accessible after migrating).
- Verified: Blocking checkout progress until T&Cs accepted via official extensibility route (vs JS hacks).
- Verified: Branding via Checkout Branding API (fonts/styling) without editing checkout theme code.
Source: https://www.wemakewebsites.com/blog/a-closer-look-hyperx-shopify-checkout-extensibility

## How this affects your theme work
- Inference: Keep theme code clean of checkout hacks; treat checkout customization as an app/extension layer.
- Inference: Build “hooks” in the theme UI to support bundling/upsell narratives, but implement checkout logic via extensibility.

