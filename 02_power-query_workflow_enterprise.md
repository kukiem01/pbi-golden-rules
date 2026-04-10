# 02) Power Query Workflow For Enterprise Models

## Scope
- Profile: `Enterprise / Shared Model`
- Use this document for shared, reusable, team-maintained, or governed models.

## Goal
- Keep Power Query readable, traceable, and maintainable across teams.
- Separate technical workflow structure from user-facing model semantics.

## Query Groups
- SHOULD: Use query groups to make lineage predictable.
- SHOULD: Use the following group layout for enterprise projects:
  - `00_Raw_Source`
  - `10_Staging`
  - `20_Model`
  - `30_Support_UI`
  - `99_Documentation`
- MAY: Omit a group when the project genuinely does not need it.

## Naming
- MUST: Use technical names only for non-loaded queries.
- SHOULD: Use these prefixes for non-loaded queries:
  - `Raw_<Thing>`
  - `Stg_<Thing>_<Step>`
  - `DOC_<NN>_<Topic>`
- MUST: Keep loaded analytical tables user-facing and business-readable.
- AVOID: Exposing `Raw_` or `Stg_` prefixes in the model field list.
- MUST: Use `_UI` naming only for disconnected or support objects covered by `04_support_tables_and_parameters.md`.

## Loading Discipline
- MUST: Set Enable Load = `OFF` for raw, staging, documentation, and helper queries not intended as model tables.
- MUST: Set Enable Load = `ON` only for final analytical tables and required support tables.
- SHOULD: Keep the loaded layer small and intentional.

## Recommended Flow
- SHOULD: Use `Raw -> Stg -> Final` when external sources, joins, shaping, or reuse make the extra layer valuable.
- MAY: Skip `Stg_` when the transformation is trivial and readability does not suffer.
- MAY: Place a standalone inline support table directly in `30_Support_UI` when there is no meaningful raw/staging split.

## Transformation Hygiene
- SHOULD: Remove unused rows and columns as early as practical.
- SHOULD: Preserve query folding when the source supports it and the model benefits from it.
- SHOULD: Apply stable, explicit data types.
- SHOULD: Prefer `Reference` over `Duplicate` for reusable logic.
- SHOULD: Delay expensive sorts, groups, pivots, and heavy joins when that keeps the query clearer or more fold-friendly.
- MUST: Follow `05_performance_import_directquery.md` when the model uses DirectQuery or has strict performance constraints.

## Documentation
- SHOULD: Use `99_Documentation` or object descriptions for project-specific caveats.
- MUST: Record any structural exception when the model intentionally breaks this workflow.
