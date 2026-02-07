# Theme architecture (OS2 fundamentals)

## Core docs
- Theme architecture overview:
  https://shopify.dev/docs/storefronts/themes/architecture
- Layouts:
  https://shopify.dev/docs/storefronts/themes/architecture/layouts
- Templates:
  https://shopify.dev/docs/storefronts/themes/architecture/templates
- JSON templates:
  https://shopify.dev/docs/storefronts/themes/architecture/templates/json-templates

## What matters when extending Skeleton
- Layout = outer wrapper; templates render inside it.
- Prefer JSON templates so merchants can add/remove/reorder sections in the editor.
- Keep responsibilities: sections = page modules; snippets = reusable partials; assets = CSS/JS.

