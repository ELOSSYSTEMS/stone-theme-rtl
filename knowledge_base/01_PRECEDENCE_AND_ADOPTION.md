# Precedence and Adoption Protocol

## 1) Precedence Hierarchy
1. Shopify Platform Constraints (API/Liquid hard limits)
2. `/docs/` (The Project Canon)
3. `/knowledge_base/shopify_skeleton_archetype_pack/` (Shopify's own reference)
4. Other Knowledge Base Packs

## 2) The "Wall of Adoption"
Knowledge does not become a requirement by osmosis. 
To adopt a pattern or rule from the Knowledge Base:

1. **Verify**: Confirm it fits the project spec in `/docs/00_MASTER_SPEC.md`.
2. **Document**: Write the rule into the appropriate `/docs/` file (e.g. `01_ARCHITECTURE_CONTRACT.md` or `06_DESIGN_TOKENS.md`).
3. **Log**: Record the decision in `/docs/04_CHANGELOG_DECISIONS.md` if it changes scope or architecture.

Until these 3 steps are done, the KB pattern is just a suggestion.
