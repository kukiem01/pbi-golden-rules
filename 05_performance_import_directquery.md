# 05) Performance: Import And DirectQuery

## Scope
- Profiles: `Universal Baseline` and `Situational Pattern`
- Use the DirectQuery section only when the model actually uses DirectQuery or composite storage modes.

## Storage Mode Choice
- SHOULD: Prefer Import mode by default.
- MAY: Use DirectQuery only when freshness, scale, or governance requirements make Import unsuitable.
- MAY: Use Dual or composite patterns only when the benefit is clear and tested.
- MUST: Document why the model is not pure Import when DirectQuery or composite storage is selected.

## Query Folding Baseline
- SHOULD: Preserve query folding when the source supports it and the model benefits from it.
- SHOULD: Keep fold-friendly transforms early when practical:
  - column selection
  - row filters
  - simple renames
  - stable type assignments
- SHOULD: Move heavy joins, pivots, groups, and complex reshaping later or upstream when that improves performance and maintainability.
- MUST: Validate folding for large models, DirectQuery models, and incremental refresh setups. Do not assume.

## DirectQuery
- MUST: Treat DirectQuery as a separate design mode with stricter constraints than Import.
- MUST: Keep Power Query steps simple and foldable.
- SHOULD: Push heavy transformations upstream into views, warehouse objects, or other source-side preparation.
- MAY: Keep a `Raw -> Stg -> Final` structure only when the final loaded query still folds and the structure adds clarity.
- AVOID: High-cardinality text fields in heavily used visuals when a better design exists.
- MUST: Validate behavior with diagnostics, source query history, or equivalent tooling.
- MUST: Test the real report experience, not only the semantic model design.

## Composite And Dual
- MAY: Use Dual mode only when justified and tested.
- SHOULD: Re-evaluate whether aggregation tables, import dimensions, or other hybrid patterns can simplify the design.
- MUST: Explain any non-obvious storage-mode choice in project documentation.

## Cross-References
- For team Power Query workflow, see `02_power-query_workflow_enterprise.md`.
- For incremental refresh, see `06_incremental_refresh.md`.
