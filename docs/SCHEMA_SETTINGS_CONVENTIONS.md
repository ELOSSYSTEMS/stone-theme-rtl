/docs/SCHEMA_SETTINGS_CONVENTIONS.md
# SCHEMA_SETTINGS_CONVENTIONS — Theme Editor UX Rules (Hebrew-first)
Version: 0.1  
Goal: A consistent, premium, Hebrew-first Theme Editor experience.

## 0) Rules
- All schema labels, infos, and option labels must be `t:` keys.
- Keep settings minimal and predictable.
- Group settings into logical “header” groups where supported.

## 1) Grouping Pattern (Recommended)
Each section schema uses these groups where applicable:
1) Content
2) Layout
3) Style
4) Behavior
5) Advanced (rare)

## 2) Setting Naming Conventions
- IDs in English snake_case.
- Labels in Hebrew via `t:` keys.
Example:
- id: `heading`
- label: `t:sections.home_hero.settings.heading.label`

## 3) Default Values Philosophy
- Defaults must look premium out of the box.
- Prefer conservative behaviors:
  - autoplay off
  - sticky off unless essential
  - animations minimal

## 4) Blocks vs Settings (When to Use Which)
Use blocks when:
- merchant will add multiple repeated items (trust items, testimonials)
Use settings when:
- single values (heading, button text, alignment)

## 5) Safe Setting Types
- text, textarea, richtext (careful)
- select (preferred for controlled variants)
- checkbox
- range (for spacing/size, but keep minimal)
- image_picker

Avoid:
- too many ranges (creates chaos)
- freeform HTML fields (risk)

## 6) Hebrew Copy Style in Editor
- Labels: short, clear nouns.
- Info/help text: 1 sentence max, neutral tone.
- Avoid emojis in editor UI.

## 7) Schema QA
- No missing `t:` keys
- No duplicated label keys for different settings
- Editor loads without schema errors

END

