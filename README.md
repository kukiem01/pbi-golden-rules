# Power BI Standards (Repo Docs)

## Purpose
- Provide a single, consistent set of rules for:
  - Power Query (ETL) structure and naming
  - Semantic model design (relationships, star schema)
  - Date table and time intelligence baseline
  - Measure organization
  - Disconnected/support tables in 30_Support_UI
  - Performance rules (DirectQuery + folding + incremental refresh)
  - AI/Q&A/Copilot metadata hygiene

## How to use
- Apply these rules to all PBIX / semantic models.
- If a rule conflicts with a specific project constraint:
  - Document the exception next to the affected query/table/measure.

## File index
- `01_power-query_etl.md`
- `02_semantic-model_design.md`
- `03_measures_organization.md`
- `04_ui_disconnected_tables.md`
- `05_performance_directquery_incremental.md`
- `06_ai_qa_copilot_metadata.md`
