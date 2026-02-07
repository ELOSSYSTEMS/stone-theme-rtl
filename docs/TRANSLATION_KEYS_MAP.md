/docs/TRANSLATION_KEYS_MAP.md
# TRANSLATION_KEYS_MAP — i18n Namespace Governance
Version: 0.1  
Goal: Keep translation keys consistent, discoverable, and non-duplicative.

## 0) Rules
- No ad-hoc keys like `text_1`, `label_2`.
- Namespaces must map to components/areas.
- Avoid duplicate meaning across different keys.

## 1) Files
Storefront:
- `locales/he.json`
- `locales/en.default.json`

Schema (Theme editor UI):
- `locales/he.schema.json`
- `locales/en.default.schema.json`

## 2) Namespace Conventions
Use these namespaces consistently:

Global:
- `a11y.*`
- `common.*`
- `buttons.*`
- `forms.*`
- `errors.*`
- `states.*`

Shell:
- `header.*`
- `footer.*`
- `nav.*`

Home:
- `home.hero.*`
- `home.collections.*`
- `home.products.*`
- `home.editorial.*`
- `manifesto.*`
- `ugc.*`
- `testimonials.*`
- `trust.*`

Collection:
- `collection.*`
- `filters.*`
- `sorting.*`

Product:
- `product.*`
- `variants.*`
- `accordion.*`
- `upsell.*`

Cart:
- `cart.*`
- `drawer.*`
- `checkout.*`

Israel Differentiators:
- `wa.*` (WhatsApp)
- `delivery.*`
- `gift.*`
- `holiday.*`

## 3) Key Naming Patterns
- Use nouns for labels: `buttons.add_to_cart`
- Use verbs for actions: `buttons.continue_shopping`
- Use state keys for statuses: `states.sold_out`
- Avoid punctuation in keys.

## 4) Ownership Rules
- Each section owns its namespace.
- If a key is used globally, it goes under `common.*` or a domain like `buttons.*`.

## 5) Anti-Patterns (Forbidden)
- Copy-paste keys across namespaces with different meanings.
- Hardcoding Hebrew strings in schema or Liquid for system UI.
- Using English phrases in Hebrew file unless intended as brand term.

END

