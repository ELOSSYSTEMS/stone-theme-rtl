# Core workflow patterns (component-first)

Transferable patterns you can apply to a Skeleton-based theme:

## 1) Separation of concerns
- Component library (reusable, versioned)
- Theme project (composition, merchant defaults, branding)

## 2) Isolation-first development
- Build/test components in an isolated environment (Explorer approach).
- Only merge into the main theme after stability.

## 3) Tooling as a thin layer
- Prefer browser-native + Shopify-native features.
- Keep JS minimal and scoped.

## 4) Regression reduction
- Use linters (Theme Check configs)
- Consider automated browser tests (Playwright seen in reference-components repo tree)

Official anchors:
- Devkit README: https://raw.githubusercontent.com/archetype-themes/devkit/main/README.md
- Getting Started overview: https://raw.githubusercontent.com/archetype-themes/devkit/main/1.%20Getting%20Started/Overview.md

