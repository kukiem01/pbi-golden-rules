# 06) Incremental Refresh

## Scope
- Profile: `Situational Pattern`
- Use this document only when a published model uses incremental refresh.

## Goal
- Apply incremental refresh consistently and only where it adds real value.

## When To Use
- MAY: Use incremental refresh for large fact-like tables in published semantic models.
- AVOID: Treating incremental refresh as a baseline requirement for every model.
- SHOULD: Confirm that the model is deployed in a context where the feature can actually be used and operated.

## Required Setup
- MUST: Configure the policy on the final loaded table.
- MUST: Apply the `RangeStart` / `RangeEnd` filter as early as possible in the query chain.
- MUST: Keep the date or datetime filter foldable.
- MUST: Use a safe boundary pattern:
  - `DateTime >= RangeStart`
  - `DateTime < RangeEnd`
- SHOULD: Configure Detect Data Changes only when a reliable last-update column exists.

## Validation
- MUST: Verify query folding before publish.
- MUST: Test refresh behavior with realistic data volume.
- SHOULD: Document the partition rationale and any special assumptions in project documentation.

## Cross-References
- For storage-mode and folding guidance, see `05_performance_import_directquery.md`.
- For enterprise Power Query workflow, see `02_power-query_workflow_enterprise.md`.
