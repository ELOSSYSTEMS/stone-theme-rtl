# RTL + i18n Lessons (WMW Public Material)

Primary article:
- “Unlocking Global E-commerce: How to Set up Translation for Your Shopify Store”
  https://www.wemakewebsites.com/blog/internationalization-translation-shopifyplus

Supporting article:
- “Everything You Need to Know About Shopify Markets”
  https://www.wemakewebsites.com/blog/everything-you-need-to-know-about-shopify-markets

## Translation approaches
- Verified: They outline machine translation, professional translation, and a hybrid approach.
  Source: https://www.wemakewebsites.com/blog/internationalization-translation-shopifyplus
- Verified: They discuss Shopify’s Translate & Adapt app using Shopify’s Translations API, and mention limits (e.g., metafields/tags/URLs not translated; some languages not available at the time of writing).
  Source: https://www.wemakewebsites.com/blog/internationalization-translation-shopifyplus

## Server-side vs client-side translations
- Verified: They compare server-side (Translations API; SEO and first-render advantages) vs client-side (post-render; can affect speed/SEO).
  Source: https://www.wemakewebsites.com/blog/internationalization-translation-shopifyplus

## RTL handling and CSS logical properties (high relevance)
- Verified: They explicitly discuss RTL languages and recommend CSS Logical Properties to support both text directions with minimal changes (inline-start/block-start, etc.), and using the direction attribute to switch RTL/LTR.
  Source: https://www.wemakewebsites.com/blog/internationalization-translation-shopifyplus

## Shopify Markets (single vs multi-store)
- Verified: They discuss tradeoffs of multi-store vs single store, and note Markets can centralize multi-currency, multi-language, domains, etc.
  Source: https://www.wemakewebsites.com/blog/everything-you-need-to-know-about-shopify-markets
- Verified: They note: “Display different theme content to different countries using Liquid.”
  Source: https://www.wemakewebsites.com/blog/everything-you-need-to-know-about-shopify-markets

## Concrete implementation rules you can hand to your IDE (STONE RTL)
- Inference: RTL-first CSS rule-set:
  - Prefer logical properties (margin-inline-start, padding-inline-end, inset-inline-start, text-align: start)
  - Avoid left/right in layout CSS; allow direction-driven flipping
  - Treat icons/arrows as “directional assets” and define mirror behavior
- Inference: i18n text strategy:
  - Put all user-facing strings in locale files where possible
  - Keep schema labels/option names localized (he/en)
  - For dynamic content, prefer Translations API compatible mechanisms

