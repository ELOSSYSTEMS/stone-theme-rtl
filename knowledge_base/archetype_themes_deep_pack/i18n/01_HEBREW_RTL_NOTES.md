# Hebrew/RTL considerations (project-specific)

This is not Archetype-specific code—these are integration notes when applying Archetype patterns to an RTL/Hebrew theme.

Rules:
- Use CSS logical properties (margin/padding inline, etc.) to avoid left/right hardcoding.
- Isolate LTR islands: prices, SKUs, URLs, emails.
- Mirror directional icons where meaning implies direction (arrows/chevrons).
- Keep focus order logical in RTL layouts (a11y).

