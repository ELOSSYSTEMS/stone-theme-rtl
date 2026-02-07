# Tech Stack Selection Notes (WMW Public Material)

Primary article:
- “Creating The Perfect E-Commerce Tech Stack”
  https://www.wemakewebsites.com/blog/creating-the-perfect-e-commerce-tech-stack

## How they frame stack selection
- Verified: They argue the tech stack should match project size, timeline, and complexity.
- Verified: They warn against overloading the stack and increasing technical debt.
- Verified: They recommend reassessing the stack over time as the business grows.
Source: https://www.wemakewebsites.com/blog/creating-the-perfect-e-commerce-tech-stack

## Extractable decision heuristic (for your IDE)
- Inference: A 4-question filter per app/tool:
  1) Which KPI does it move? (AOV, CR, speed, ops cost)
  2) Does it add render cost / CLS risk?
  3) Does it integrate with the translation strategy (server-side vs post-render)?
  4) Can Shopify native features replace it (to reduce tech debt)?

## “Slim first” defaults (good for a solo builder)
- Inference:
  - Start with Shopify-native where possible
  - Add only when you can define measurable gain and rollback plan

