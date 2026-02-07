# Locales, i18n, RTL/Hebrew

## Core docs
- Locales overview:
  https://shopify.dev/docs/storefronts/themes/architecture/locales
- Storefront locale files:
  https://shopify.dev/docs/storefronts/themes/architecture/locales/storefront-locale-files
- Schema locale files:
  https://shopify.dev/docs/storefronts/themes/architecture/locales/schema-locale-files
- `translate` / `t` filter:
  https://shopify.dev/docs/api/liquid/filters/translate

## RTL implementation reminders (project-specific)
- Use CSS logical properties instead of left/right.
- Treat LTR islands (numbers, SKUs, URLs) explicitly.
- Ensure icons that imply direction mirror in RTL.

