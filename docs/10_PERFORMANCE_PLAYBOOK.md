/docs/10_PERFORMANCE_PLAYBOOK.md
# 10_PERFORMANCE_PLAYBOOK — Performance Rules & Patterns
Version: 0.1  
Goal: Maintain Theme Store-level performance with minimal CLS and minimal JS.

## 0) Performance Principles
- Ship less JS.
- Reserve space for media to prevent CLS.
- Scope assets to components.
- Prefer server-rendered Liquid over JS rendering.

## 1) Global Budget Rules (Guidelines)
- `assets/critical.css` contains only universal tokens and primitives.
- Site-wide JS should be avoided; if needed, it must be tiny and justified.
- No heavy slider/filter libraries without decision log entry.

## 2) CLS Prevention (Hard Rules)
- Hero: reserve height (min-height or aspect ratio strategy)
- Product gallery: reserve aspect ratio for main media
- Cart drawer: opening must not shift layout; use fixed positioning

## 3) Image Rules
- Always set width/height or aspect ratio behavior.
- Use responsive `srcset` where applicable.
- Lazy-load non-critical images.
- Avoid background-image for critical imagery unless necessary.

## 4) JS Patterns Allowed
- Minimal drawer controller
- Minimal slider controller
- Predictive search controller (optional)

Required:
- Event delegation where possible
- Clean teardown on section reloads (Theme Editor)

## 5) JS Patterns Forbidden
- Large frameworks
- Animations that trigger layout thrash
- Continuous polling
- Multiple competing focus traps

## 6) Theme Editor Performance
- Settings changes should not cause full-page thrash.
- Avoid forced synchronous layout in scripts.

## 7) Performance QA Checklist
For each major component:
- Does it introduce CLS?
- Does it add site-wide JS?
- Does it delay interaction?
- Does it load images efficiently?

If any answer is “yes,” mitigate or log a decision.

END

