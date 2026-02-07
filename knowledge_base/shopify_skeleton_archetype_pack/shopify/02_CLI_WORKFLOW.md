# Shopify CLI workflow (themes)

## Primary docs
- Theme commands index:
  https://shopify.dev/docs/api/shopify-cli/theme
- `theme dev`:
  https://shopify.dev/docs/api/shopify-cli/theme/theme-dev
- `theme init` (Skeleton default):
  https://shopify.dev/docs/api/shopify-cli/theme/theme-init
- Environments:
  https://shopify.dev/docs/storefronts/themes/tools/cli/environments
- Multi-environment theme commands changelog:
  https://shopify.dev/changelog/multi-environment-theme-commands-shopify-cli

## Operational pattern (suggested)
- Dev: `shopify theme dev`
- Validate: `shopify theme check`
- Stage: push to a staging theme/environment
- Release: publish via admin flow or CLI-supported publish step (per docs)

