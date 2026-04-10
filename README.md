# Power BI Standards

## Purpose
- Provide one maintainable ruleset for Power BI developers working on local PBIX files, shared semantic models, and advanced patterns.
- Keep the standards scalable, future-aware, and explicit about where a rule applies.

## Norm Levels
- `MUST` - Required for the stated scope.
- `SHOULD` - Strong default; breaking it requires a reason.
- `MAY` - Optional pattern.
- `AVOID` - Use only with clear justification.
- `EXCEPTION` - Recorded departure from a `MUST`, `SHOULD`, or `AVOID`.

## Scope Profiles
- `Universal Baseline`
  - Applies to all PBIX files and semantic models.
  - Covers naming, relationships, visibility, formatting, and low-ambiguity modeling basics.
- `Enterprise / Shared Model`
  - Applies to reusable, published, team-owned, or governed models.
  - Adds workflow discipline, stronger metadata expectations, and stricter organization rules.
- `Situational Pattern`
  - Applies only when a specific design pattern is chosen.
  - Covers DirectQuery, incremental refresh, support tables, field parameters, and other advanced cases.
- `Legacy`
  - Transitional guidance only.
  - Use for patterns being phased out or maintained only for existing workloads.

## How To Use
- Always apply `01_universal_modeling_baseline.md`.
- Add enterprise rules when the model is shared, reusable, published, or team-maintained.
- Add situational documents only when the model actually uses that pattern.
- Treat `appendix_legacy_qna.md` as transition guidance only. Q&A experiences are being retired in December 2026.

## Exception Record
Record each exception next to the affected object or in project documentation.

- `Rule ID`
- `Object`
- `Scope`
- `Reason`
- `Risk`
- `Owner`
- `Review date`
- `Mitigation`

## File Index
- `01_universal_modeling_baseline.md`
  - Universal modeling baseline for all PBIX files and semantic models.
- `02_power-query_workflow_enterprise.md`
  - Enterprise Power Query workflow, naming, and load discipline.
- `03_measures_and_semantics.md`
  - Measure strategy, naming, folders, and semantic consistency.
- `04_support_tables_and_parameters.md`
  - Disconnected support tables, `_UI` naming, and field parameter guardrails.
- `05_performance_import_directquery.md`
  - Import defaults, query folding, and DirectQuery-specific rules.
- `06_incremental_refresh.md`
  - Incremental refresh rules for applicable published models.
- `07_ai_metadata_copilot_readiness.md`
  - Metadata hygiene and Copilot-oriented model readiness.
- `appendix_legacy_qna.md`
  - Legacy Q&A guidance for teams still supporting Q&A before December 2026 retirement.
