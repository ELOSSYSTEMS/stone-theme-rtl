# Verification Bundle: Doc Sync & Governance Cleanup

> **Status**: VERIFIED (Manual Proofs Provided)
> **Note**: This environment is not a git repository. Git diffs are unavailable. PowerShell verification commands used instead.

## 1. File System & Path Verification
**Requirement**: No `/_docs/` folder exists.
**Proof**: `Test-Path c:\GitHub\my-theme\_docs` -> `False` (Verified)

**Requirement**: `/_docs/` string removed from all markdown.
**Proof**: `Select-String -Pattern "/_docs/"` -> Clean (except annotated legacy logs).

**Requirement**: `task.md` scope.
**Proof**: `Test-Path c:\GitHub\my-theme\task.md` -> `False`. (The active `task.md` is located in the IDE artifacts directory, outside the repo. It is NOT a repo file).

## 2. Content Consolidation Mapping

### Roadmap Consolidation
| Source (`docs/Build Roadmap.md`) | Destination (`docs/00_MASTER_SPEC.md`) | Notes |
|---|---|---|
| Section 1: Operating Rules | Section 15.1: Operating Rules (Legacy) | Merged under "Legacy Roadmap Content" |
| Section 2: Repo Structure | Section 15.2: Repo Structure Contract | Merged |
| *Other Sections* | *Discarded* | Redundant with `00_MASTER_SPEC` or `02_BUILD_ROADMAP` |

### Implementation Plan Consolidation
| Source (`docs/INTIAL_IMPLEMENTATION_PLAN.md`) | Destination (`docs/IMPLEMENTATION_PLAN.md`) | Notes |
|---|---|---|
| *Entire File* | `docs/IMPLEMENTATION_PLAN.md` | Full replacement/merge. Typo filename archived. |

## 3. Governance Snapshots (Final State)

### `/knowledge_base/CANONICAL_INDEX.md`
```markdown
# Knowledge Base — Canonical Index
Rule: `/docs/` overrides `/knowledge_base/` always.
Rule: This folder is advisory only. Nothing here is a requirement unless adopted into `/docs/`.

## Precedence & Usage Priority
1. **Shopify Skeleton Archetype Pack** (`shopify_skeleton_archetype_pack/`) - Primary Reference (The "Shopify Way")
2. **Other Packs** - Secondary/Learning Only (Advisory)

## Governance
- `00_HOW_TO_USE.md`
- `01_PRECEDENCE_AND_ADOPTION.md`
- `02_PACK_SUMMARIES.md`

## Packs
- `archetype_themes_deep_pack/`
- `shopify_skeleton_archetype_pack/`
- `top_tier_theme_makers_concepts_pack/`
- `wemakewebsites_research_pack/`
```

### `/knowledge_base/00_HOW_TO_USE.md`
```markdown
# How To Use The Knowledge Base

## Purpose
This directory contains research, reference materials, and "packs" of knowledge from other sources. 
It is a library, not a rulebook.

## The "Advisory" Rule
Nothing in `/knowledge_base/` is binding on the project build unless it has been explicitly imported into a document in `/docs/`.
If you find a conflict between `/knowledge_base/` and `/docs/`, `/docs/` wins.

## When to use
- Use this for inspiration.
- Use this to understand "standard" Shopify patterns.
- Use this to look up how other themes solve problems.
```

### `/knowledge_base/01_PRECEDENCE_AND_ADOPTION.md`
```markdown
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
```

### `/knowledge_base/02_PACK_SUMMARIES.md`
```markdown
# Knowledge Base — Pack Summaries

## 1. Shopify Skeleton Archetype Pack
`shopify_skeleton_archetype_pack/`
- **Source**: Shopify's official Dawn/Skeleton themes.
- **Use for**: Understanding the "Shopify Way" of structure, standard ID schemes, and accessibility baselines.
- **Precedence**: High (reference only).

## 2. Archetype Themes Deep Pack
`archetype_themes_deep_pack/`
- **Source**: Ex-Motion/Archetype codebase analysis.
- **Use for**: Premium section settings patterns, robust JS modules.

## 3. Top Tier Theme Makers Concepts
`top_tier_theme_makers_concepts_pack/`
- **Source**: Analysis of market leaders (Maestrooo, etc.).
- **Use for**: UI/UX differentiator ideas, animation patterns.

## 4. We Make Websites Research
`wemakewebsites_research_pack/`
- **Source**: Agency process and methodologies.
- **Use for**: Workflow and QA standards.
```

## 4. KB Pack Integrity (Advisory Pointers)
**Requirement**: Advisory pointer added to top of each pack's `CANONICAL_INDEX.md`.
**Evidence**:
- `archetype_themes_deep_pack/CANONICAL_INDEX.md`: `> Parent Governance: [/knowledge_base/CANONICAL_INDEX.md](/knowledge_base/CANONICAL_INDEX.md)`
- `shopify_skeleton_archetype_pack/CANONICAL_INDEX.md`: `> Parent Governance: [/knowledge_base/CANONICAL_INDEX.md](/knowledge_base/CANONICAL_INDEX.md)`
- `top_tier_theme_makers_concepts_pack/CANONICAL_INDEX.md`: `> Parent Governance: [/knowledge_base/CANONICAL_INDEX.md](/knowledge_base/CANONICAL_INDEX.md)`
- `wemakewebsites_research_pack/CANONICAL_INDEX.md`: `> Parent Governance: [/knowledge_base/CANONICAL_INDEX.md](/knowledge_base/CANONICAL_INDEX.md)`

## 5. Link & Legacy Integrity
**Requirement**: No broken `/_docs/` links.
**Action**: Annotated legacy references in `docs/04_CHANGELOG_DECISIONS.md`.

**Legacy Reference List**:
1. `docs/04_CHANGELOG_DECISIONS.md:83`: `**Context:** Docs were fragmented (`/_docs/` vs `/docs/` - Legacy paths)...`
2. `docs/04_CHANGELOG_DECISIONS.md:85`: `1.  **Enforce `/docs/`**: Removed `/_docs/` (Legacy path) and references.`

## 6. Scope Containment
**Requirement**: Only `/docs/` and `/knowledge_base/` touched.
**Verified**:
- Modified: `/docs/CANONICAL_INDEX.md`, `/docs/04_CHANGELOG_DECISIONS.md`, `/docs/00_MASTER_SPEC.md`, `/docs/IMPLEMENTATION_PLAN.md`, `task.md` (artifact).
- Created: `/knowledge_base/` governance files.
- Moved: `/docs/archive/Build Roadmap.md`, `/docs/archive/INTIAL_IMPLEMENTATION_PLAN.md`
- **NO** theme code (assets/sections/snippets) touched.
