# Support boundaries and app risk (what vendors publicly refuse)

Top theme makers publish strict rules about what they support. Treat these as **design constraints**.

---

## 1) Support scope: original theme + configuration (Verified)
- Pixel Union: supports theme features/functionality/configuration and bugs in original state; does not provide custom feature development/design services.  
  Source: https://support.pixelunion.net/hc/en-us/articles/360022344033-Pixel-Union-Support-Policy citeturn2search4
- Switch: covers general questions and bug fixes in setup; does not cover custom coding requests.  
  Source: https://switchthemes.co/support/policy citeturn2search1
- Clean Canvas: free support limited to theme as originally provided; custom features/coding/apps not covered.  
  Source: https://support.cleancanvas.co.uk/hc/en-us/articles/12067015902237-Support-terms citeturn3search6
- Fluorescent: supports unmodified theme use; not third-party app integrations or issues from modifications.  
  Source: https://help.fluorescent.co/ira/support/support-policy citeturn1search1
- Out of the Sandbox: does not support removing/updating customizations; cannot transfer customizations to new versions.  
  Source: https://outofthesandbox.com/pages/support citeturn0search0

---

## 2) Apps: “first contact the app developer” (Verified)
- Fluorescent states they cannot guarantee compatibility of all apps; app developer should be first contact; apps can inject code that remains after deletion.  
  Source: https://help.fluorescent.co/ira/support/support-policy citeturn1search1

---

## 3) Shopify’s own boundary (Verified)
Shopify notes it can’t help with troubleshooting themes that contain significant code changes or third-party code (including AI-generated blocks).  
Source: https://help.shopify.com/en/manual/online-store/themes/theme-support citeturn3search4

---

## How to use this in STONE RTL (enforceable)
- Treat “apps that inject code” as high-risk changes requiring:
  - performance budget check
  - rollback plan
- Prefer Shopify-native features (filters, swatches, translations) to reduce app coupling.
- When an app is required, implement an “integration boundary”:
  - one snippet or section handles the app hook
  - no app logic scattered across multiple core files

