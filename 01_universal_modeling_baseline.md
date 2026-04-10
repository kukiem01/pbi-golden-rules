# 01) Universal Modeling Baseline

## Scope
- Profile: `Universal Baseline`
- Applies to all PBIX files and semantic models unless a situational document states otherwise.

## Goal
- Keep models understandable, scalable, and low-ambiguity for report authors, consumers, and AI experiences.

## Model Shape
- SHOULD: Prefer a star schema where practical.
- MUST: Keep dimensions primarily for filtering and grouping, and facts primarily for events, balances, or transactions.
- MUST: Avoid ambiguous filter paths.
- SHOULD: Use single-direction relationships by default.
- AVOID: Bi-directional relationships unless a specific requirement justifies them and the impact is understood.
- AVOID: Many-to-many relationships when a bridge pattern can solve the problem more clearly.

## Relationship Quality
- MUST: Ensure the dimension-side key is unique for `1:*` relationships.
- MUST: Avoid null keys on the dimension side.
- SHOULD: Use an explicit "unknown" member strategy when source data is incomplete.
- MUST: Validate relationship direction and active/inactive behavior intentionally.

## Date Strategy
- MAY: Use Auto date/time for simple, local, ad hoc import models with straightforward calendar analysis.
- SHOULD: Use one explicit Date table for reusable, shared, multi-fact, paginated, Analyze in Excel, or AI-facing models.
- MUST: Keep the Date table contiguous and mark it properly when an explicit Date table is used.
- SHOULD: Connect Date to facts with single-direction relationships by default.
- MAY: Use inactive relationships with `USERELATIONSHIP()` for alternate date roles when that keeps the model simpler.
- MAY: Use role-playing Date tables when UX or performance requires clearly separate date roles.
- AVOID: Auto date/time in enterprise or shared semantic models.

## Naming
- MUST: Use business-readable names for user-facing tables, columns, and measures.
- MUST: Distinguish similarly named fields across tables when ambiguity would hurt self-service or AI interpretation.
- AVOID: Technical prefixes on user-facing analytical tables.
- SHOULD: Use Title Case with spaces for user-facing object names.

## Visibility
- MUST: Hide surrogate keys, relationship keys, technical IDs, and helper columns that are not intended for report authors.
- SHOULD: Keep only user-facing attributes, hierarchies, and intentional self-service fields visible.
- MUST: Hide purely technical support columns unless a situational document explicitly requires visibility.

## Measures And Formatting
- MUST: Put currency, percent, decimal, and date display intent in model formatting when possible.
- MUST: Keep business-critical metrics as explicit measures.
- MAY: Rely on implicit measures in small local PBIX files when the model is not intended for reuse.
- AVOID: Formatting numeric business values as text unless there is a clear reporting need.

## Metadata Baseline
- MUST: Use correct data types.
- SHOULD: Set data categories for geography and similar fields.
- MUST: Set IDs and key-like fields to `Do not summarize`.
- SHOULD: Add descriptions for non-obvious tables, columns, and measures, especially when the model is published or reused.

## References
- For Power Query workflow in team-owned models, see `02_power-query_workflow_enterprise.md`.
- For support tables and field parameters, see `04_support_tables_and_parameters.md`.
- For performance and DirectQuery, see `05_performance_import_directquery.md`.
- For AI metadata and Copilot readiness, see `07_ai_metadata_copilot_readiness.md`.
