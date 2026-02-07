# How to use this pack for IDE/LLM

Recommended ingestion approach:
1. Load `CANONICAL_INDEX.md` first (acts as a router).
2. Prioritize `devkit/*` for workflow patterns and tooling ideas.
3. Use `help_center/*` as “feature expectation specs” to define acceptance criteria.
4. Use `ops/*` to set governance rules: avoid divergence, isolate customizations, keep upgrades possible.

Suggested IDE behavior (enforceable rules):
- Prefer small diffs and file-scoped changes.
- Keep “system code” (reusable components) separated from “theme composition.”
- Avoid global refactors; focus on patchable, reversible changes.

