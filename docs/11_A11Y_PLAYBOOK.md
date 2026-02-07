/docs/11_A11Y_PLAYBOOK.md
# 11_A11Y_PLAYBOOK — Accessibility Patterns & Requirements
Version: 0.1  
Goal: Pass Theme Store expectations and deliver usable UI for all users.

## 0) Core Requirements
- Keyboard navigation must work everywhere.
- Focus must be visible.
- Modals/drawers must manage focus correctly.
- Controls must have accessible names.

## 1) Focus & Keyboard Patterns
### 1.1 Header and Navigation
- Menu trigger is keyboard focusable.
- Opening drawer moves focus into drawer.
- Closing drawer returns focus to trigger.
- Escape closes drawer.

### 1.2 Drawer / Modal Focus Trap
When open:
- Trap tab within drawer
- Close on Escape
- Prevent background scroll (mobile)
- Overlay click closes (optional but recommended)

### 1.3 Accordions
- Toggle is a button
- `aria-expanded` updates
- Content has an ID referenced by `aria-controls`

## 2) Accessible Names
- Icon-only buttons must have `aria-label`.
Examples:
- Search button: `aria-label="חיפוש"`
- Cart button: `aria-label="עגלה"`

## 3) RTL-Specific A11y Notes
- Focus order must match visual order, not DOM hacks.
- Mirrored icons must not change button semantics.
- Ensure “back” buttons remain understandable in Hebrew labels.

## 4) Headings Hierarchy
- One H1 per page template.
- Section headings use H2/H3 appropriately.
- Do not skip levels.

## 5) Color Contrast & Motion
- Ensure text contrast is readable in defaults.
- Provide reduced motion support if feasible for sliders.

## 6) Forms
- Inputs must have labels.
- Error messages must associate to fields (aria-describedby).
- Required fields indicated.

## 7) A11y QA Checklist
For each feature:
- Keyboard test: tab through all controls
- Screen-reader sanity: buttons have names
- Focus visible: always
- Escape closes overlays
- No focus lost behind overlays

Log any exceptions in 04_CHANGELOG_DECISIONS.md.

END

