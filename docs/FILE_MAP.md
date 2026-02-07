/docs/FILE_MAP.md
# FILE_MAP — Repo Ownership Map (Where Things Live)
Version: 0.1  
Goal: Prevent edits in the wrong place. Make the IDE fast and precise.

## 0) Golden Rule
If you can’t name the correct file to edit in one sentence → STOP and consult this map + Architecture Contract.

## 1) Top-Level
- `/GLOBAL_ANTIGRAVITY_RULES.md`  
  Operating contract for all agents.

- `/docs/`  
  Canonical docs + runbooks. Always update docs when behavior changes.

- `/theme/<THEME_NAME>/`  
  Canonical theme workspace (single source of code truth).  
  Anything outside is non-canonical unless promoted.

## 2) Theme Folders (Shopify)
### `layout/`
- Owns global HTML shell and critical includes.
- Primary file: `layout/theme.liquid`
- **High-risk:** changes here can break the whole storefront.
- Rule: minimize changes, scope assets.

### `templates/`
- JSON templates defining section stack per page type.
- Examples: `templates/index.json`, `templates/product.json`, `templates/collection.json`
- **High-risk:** missing section types break editor/pages.

### `sections/`
- Major page components with schema.
- Rule: new sections must be registered in `05_SECTION_INVENTORY.md`.

### `snippets/`
- Reusable partials used by sections.
- Rule: snippets must render safely even if variables missing.

### `assets/`
- CSS/JS/images/fonts.
- Rules:
  - scope CSS/JS to components whenever possible
  - avoid global JS
  - tokens/primitives in `assets/critical.css` only

### `config/`
- Theme settings schema and data.
- Files:
  - `config/settings_schema.json` (structure of settings)
  - `config/settings_data.json` (defaults)
- **Extremely high-risk:** accidental corruption breaks theme editor.

### `locales/`
- Translations. Always maintain:
  - `he.json` + `en.default.json`
  - `he.schema.json` + `en.default.schema.json`

## 3) “Do Not Touch” List (Without Explicit Objective + Backups)
- `layout/theme.liquid`
- `config/settings_schema.json`
- `config/settings_data.json`
- `templates/*.json` (bulk edits)
- Any file renames/moves across folders

## 4) Common Ownership Patterns
- UI strings:
  - Storefront text: `locales/*.(he|en).json`
  - Editor labels: `locales/*.(he|en).schema.json`
- Icons:
  - `snippets/icon-*.liquid` + `.icon--dir` mirror rules (Design Tokens)
- RTL/Bidi:
  - utility classes referenced in `09_BIDI_EDGE_CASES.md`
- Theme Styles / presets:
  - Spec in `08_THEME_STYLES_SPEC.md`
  - Implementation likely in settings data + templates defaults (must be documented)

END

