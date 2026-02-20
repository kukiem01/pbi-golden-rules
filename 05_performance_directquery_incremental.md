# 05) Performance - DirectQuery, Folding, Incremental Refresh

## Storage mode choice (first decision)
- Prefer Import mode by default
- Use DirectQuery only when requirements force it (freshness, size, governance constraints)
- For composite models, use Dual mode only when justified and tested

## Query folding (default)
- Preserve folding whenever possible
- Keep fold-friendly steps early:
  - select columns
  - filters
  - simple renames/types (connector-dependent)
- Put expensive/non-foldable operations late, or move upstream (views)

## DirectQuery (especially Databricks)
- DirectQuery relies on folding; non-foldable steps can break support or performance
- Staging (Raw → Stg → Final) is allowed **only** if the final loaded query still folds
- Using Reference does not inherently break folding; non-foldable steps do
- Reduce high-cardinality text usage in visuals where possible
- Validate with diagnostics/source query history (do not guess)

## Incremental refresh (where to implement)
- Policy is configured on the **final loaded table** (typically a fact table)
- The `RangeStart/RangeEnd` filter should be applied as early as possible in the query chain
  - ideally immediately after Source in a `Stg_` query referenced by the final table
- Keep the date filter foldable
- Use a safe boundary pattern:
  - `DateTime >= RangeStart`
  - `DateTime <  RangeEnd`
- If needed, configure Detect Data Changes with a reliable last-update column
