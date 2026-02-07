# Fluorescent — update process + “Contexts” implications

## Their update stance (Verified)
- Use Theme library notifications to add updated copies and view release notes.
- Automatic updates may apply for minor/security fixes; editor customizations are included.
- Manual update required if custom code changes exist; support does not cover manual updates/customizations/app integration.  
Source: https://help.fluorescent.co/v/spark/general/theme-updates citeturn1search0

## “Contexts” signal (Verified)
Their guide references files like:
- `header-group.context.eu.json`
- `footer-group.context.ca.json`  
This implies a pattern where multiple region-specific contexts can exist.  
Source: https://help.fluorescent.co/v/spark/general/theme-updates citeturn1search0

## Extraction (Inference)
- If you implement region/market “contexts”, you must plan file explosion and update migration strategy.
- For STONE: prefer simple, Shopify-native Markets behavior; if you add context variants, document naming and migration steps.

