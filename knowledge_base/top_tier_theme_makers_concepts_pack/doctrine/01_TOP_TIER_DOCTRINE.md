# Top-tier doctrine: the non-negotiables (distilled)

This file describes the **shared operating philosophy** visible across multiple top-tier theme makers’ public policies and guides.
Where a claim is “Verified,” it is directly supported by a cited source. “Inference” means a general rule extracted from multiple verified points.

---

## 1) Upgrades are a product feature (Verified + Inference)
**Verified signals:**
- Vendors repeatedly warn that **code changes** (by you, developers, or apps) can make updates manual and unsupported.  
  Sources:
  - Out of the Sandbox support policy (customizations complicate updates; customizations not transferred) — https://outofthesandbox.com/pages/support citeturn0search0
  - Maestrooo update guide (automatic updates only if code not edited; manual reapply of custom code; no help transferring) — https://support.maestrooo.com/article/778-updating-your-theme citeturn3search0
  - Fluorescent update guide (manual update required if code changes; support doesn’t cover manual updates/customizations) — https://help.fluorescent.co/v/spark/general/theme-updates citeturn1search0
  - Pixel Union support policy + update guides (support covers original theme; manual migration needed for custom code) — https://support.pixelunion.net/hc/en-us/articles/360022344033-Pixel-Union-Support-Policy citeturn2search4

**Inference (doctrine):**
- Treat “updateability” as a first-class requirement. If your theme cannot be updated safely, it will decay.

---

## 2) Support has hard boundaries (Verified)
**Verified signals:**
- Vendors support **built-in features and bugs in unmodified themes**, not custom coding or app integration.  
  Sources:
  - Switch support policy — https://switchthemes.co/support/policy citeturn2search1
  - Clean Canvas support terms — https://support.cleancanvas.co.uk/hc/en-us/articles/12067015902237-Support-terms citeturn3search6
  - Fluorescent support policy — https://help.fluorescent.co/ira/support/support-policy citeturn1search1
  - Out of the Sandbox support policy — https://outofthesandbox.com/pages/support citeturn0search0

**Doctrine:**
- Build your theme so you rarely need “custom code” for common tasks: expose features through settings and sections.

---

## 3) Apps are an architecture risk (Verified + Inference)
**Verified signals:**
- Vendors warn apps can inject code and create compatibility issues; they generally won’t troubleshoot those.  
  Source: Fluorescent support policy — https://help.fluorescent.co/ira/support/support-policy citeturn1search1

**Doctrine:**
- Assume third-party scripts and app injections are the largest source of regressions and performance loss.
- Isolate app placements; avoid making theme core depend on apps.

---

## 4) Accessibility is valued, but compliance guarantees are limited (Verified)
**Verified signals:**
- Maestrooo states they value accessibility and follow best practices, but do not guarantee full ADA compliance.  
  Source: Maestrooo accessibility article — https://support.maestrooo.com/article/686-accessibility-ada-a11y citeturn1search3

**Doctrine:**
- Treat keyboard navigation and semantic markup as baseline acceptance criteria.
- Do not claim full compliance unless you have audit evidence.

---

## 5) “Backups + parallel windows” is the practical migration method (Verified)
**Verified signals:**
- Vendors recommend adding an updated copy, opening both versions side-by-side, and copying settings/template configurations.  
  Sources:
  - Pixel Union manual update guide — https://support.pixelunion.net/hc/en-us/articles/360038477493-Updating-a-theme-manually citeturn3search1
  - Fluorescent manual update guide (open files; copy templates/settings) — https://help.fluorescent.co/v/spark/general/theme-updates citeturn1search0

**Doctrine:**
- “Manual update” is a controlled migration exercise, not a quick patch.

---

## Apply to STONE RTL (actionable constraints)
- Avoid touching core files unless required; keep changes section-scoped.
- Keep an explicit “customizations changelog” for every code edit.
- Build preset-like theme styles (settings bundles) so merchants don’t request code edits.

