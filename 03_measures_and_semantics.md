# 03) Measures And Semantics

## Scope
- Profiles: `Universal Baseline` and `Enterprise / Shared Model`
- Use this document for measure naming, organization, and semantic consistency.

## Goal
- Keep measures easy to find, stable to reference, and safe to maintain.

## Strategy
- MUST: Use business language for measure names.
- MUST: Keep important business metrics as explicit measures.
- SHOULD: Use one dedicated measure table in shared or reusable semantic models.
- MAY: Keep measures in fact tables or rely on implicit measures in small local PBIX files when reuse is not a goal.
- MAY: Use multiple measure tables when domain ownership requires it.
- MUST: Keep one naming and foldering standard across all measure tables if more than one exists.

## Organization
- SHOULD: Use Display Folders as the primary organization mechanism.
- SHOULD: Keep folder depth shallow.
- SHOULD: Use a stable taxonomy such as `Base`, `Time Intelligence`, `Variance`, `Ratios`, `Formatting`, or `Tooltips`.

## Naming Rules
- MUST: Use stable, readable names.
- AVOID: Technical prefixes or suffixes such as `m_`, `msr_`, or `_calc`.
- SHOULD: Use consistent suffix patterns for time and comparison measures:
  - `Sales MTD`
  - `Sales QTD`
  - `Sales YTD`
  - `Sales PY`
  - `Sales YoY`
  - `Sales YoY %`
  - `Sales Rolling 12M`
- SHOULD: End ratio and percentage measures with `%` when that improves clarity.
- SHOULD: Keep units in formatting instead of embedding them in names unless the unit is part of the business concept.

## Construction
- MUST: Create base measures first.
- MUST: Build derived measures on top of shared base measures instead of repeating business logic.
- SHOULD: Use `VAR ... RETURN` for non-trivial logic.
- MUST: Prefer `DIVIDE()` over `/` when the denominator can be zero or blank.
- SHOULD: Keep filter logic explicit and readable.

## Metadata
- SHOULD: Add descriptions for core measures in shared, published, or reused models.
- MUST: Add a description when a measure is business-critical, non-obvious, or likely to be reused by others.
- SHOULD: Capture definition, assumptions, unit, grain, and key exclusions in the description when relevant.

## Field Parameters
- MAY: Use Field Parameters for intentional user-driven switching of measures or dimensions.
- MUST: Treat Field Parameters as a situational UX pattern, not as a universal baseline.
- MUST: Store Field Parameter tables under the support table rules in `04_support_tables_and_parameters.md`.
- MUST: Provide explicit fallback measures, or another clear semantic route, when the model is AI-facing or heavily self-service.
- AVOID: Making Field Parameters the only semantic path for critical business questions.
