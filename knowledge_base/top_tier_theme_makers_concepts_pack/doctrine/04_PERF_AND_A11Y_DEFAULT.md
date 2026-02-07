# Performance + accessibility as default (vendor-grade baseline)

---

## 1) Accessibility: commitment without full guarantee (Verified)
- Maestrooo states they value accessibility and follow best practices, but do not guarantee full ADA compliance.  
  Source: https://support.maestrooo.com/article/686-accessibility-ada-a11y citeturn1search3

**Actionable baseline:**
- Keyboard navigation for menus, modals, and key interactions
- Visible focus states
- Meaningful alt text patterns for icons/images
- Avoid motion traps; provide reduced-motion support

---

## 2) Performance: protect the core from app bloat (Verified + Inference)
- Fluorescent warns that apps may inject code and cause compatibility issues.  
  Source: https://help.fluorescent.co/ira/support/support-policy citeturn1search1

**Inference doctrine:**
- Keep theme JS minimal and section-scoped.
- Avoid third-party scripts in critical rendering path.
- Reserve media space to avoid layout shifts (CLS).

---

## 3) “Editable JS / Custom Liquid / Custom Events” are attempts to reduce risky edits (Verified)
Fluorescent markets:
- “Custom Events” to add functionality without editing unfamiliar JS files
- “Custom Liquid” drag-and-drop section in editor
- “Editable JavaScript” un-minified classic build file if edits are needed  
Source: https://fluorescent.co/ citeturn1search5

**Inference:**
Top themes try to provide controlled extension points so merchants avoid editing core code.

---

## Apply to STONE RTL
- Implement safe extension points:
  - Custom Liquid section
  - Custom CSS settings for limited tweaks
  - Event hooks for integrations (documented)
- Require a11y/perf checks for every change:
  - keyboard test
  - no CLS on load
  - no console errors

