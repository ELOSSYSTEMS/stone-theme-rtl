# Upgradeability and divergence (how top theme makers structure reality)

This file turns vendor update guidance into **engineering constraints** you can enforce on your Skeleton-based theme.

---

## 1) Shopify updates are easiest when code is untouched (Verified)
- Maestrooo: automatic updates are eligible only when the theme code has not been edited by you, a developer, or apps.  
  Source: https://support.maestrooo.com/article/778-updating-your-theme citeturn3search0
- Fluorescent: manual update required if you or an app made custom code changes; support doesn’t cover manual updates/customizations.  
  Source: https://help.fluorescent.co/v/spark/general/theme-updates citeturn1search0
- Shopify Help Center: some features may not apply; manual update may be needed.  
  Source: https://help.shopify.com/en/manual/online-store/themes/managing-themes/upgrading-themes citeturn2search3

**Implication:** your theme should minimize reasons to edit code post-launch.

---

## 2) “Manual update” is a repeatable procedure (Verified)
Common pattern:
1) Add the updated theme copy to the library
2) Open both theme editors side-by-side
3) Recreate settings, templates, and section order
4) Reapply custom code where necessary
5) Reinstall apps that inject code

Sources:
- Pixel Union manual update guide — https://support.pixelunion.net/hc/en-us/articles/360038477493-Updating-a-theme-manually citeturn3search1
- Fluorescent update guide — https://help.fluorescent.co/v/spark/general/theme-updates citeturn1search0

---

## 3) Tools exist, but conflicts still happen (Verified)
- Out of the Sandbox Theme Updater comparison page claims Theme Updater can migrate manual code changes and schema changes beyond Shopify’s built-in updater.  
  Source: https://help.outofthesandbox.com/hc/en-us/articles/28069282350995-How-does-Theme-Updater-compare-to-the-built-in-Shopify-updates citeturn0search2
- Out of the Sandbox update guide notes some files still require manual resolution; conflicts are presented for manual decisions.  
  Source: https://help.outofthesandbox.com/hc/en-us/articles/115007099548-Update-your-theme-with-Theme-Updater-Pro-Plan citeturn0search4

**Doctrine:** even “smart updaters” require human review. Build your theme with upgrade-friendly boundaries.

---

## 4) Vendor support typically won’t migrate your custom code (Verified)
- Out of the Sandbox: cannot transfer customizations to new versions; recommends reverting files if needed.  
  Source: https://outofthesandbox.com/pages/support citeturn0search0
- Fluorescent: support cannot cover manual theme updates or code customizations.  
  Source: https://help.fluorescent.co/v/spark/general/theme-updates citeturn1search0
- Clean Canvas: does not provide manual update service; recommends using a developer.  
  Source: https://support.cleancanvas.co.uk/hc/en-us/articles/11596388945949-Updating-themes citeturn3search2

---

## Engineering constraints to enforce (for your IDE)
- Every code change must update a `CUSTOMIZATIONS_CHANGELOG.md` with:
  - file, change summary, reason, rollback notes
- Prefer “extension-point” snippets and isolated sections; avoid edits to core layout.
- Implement merchant needs via settings/schema before code.
- Maintain a “lab theme” copy for experiments; merge only after QA.

