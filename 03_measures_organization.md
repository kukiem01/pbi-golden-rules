# 03) Measures - Naming, Organization, Maintenance (Golden Rules)

## Goal
- Measures are easy to find, consistent to use, and safe to maintain

## Measures table strategy (default)
- Keep measures in a dedicated table (do not scatter across facts/dims)
- Recommended table names:
  - Key Measures
  - All Measures
  - Metrics
- Avoid naming the table exactly `Measures` to reduce ambiguity with default tool behaviors

## Allowed exception (large/domain models)
- Multiple measure tables are allowed when model/domain ownership requires it
- If used, keep one shared naming/folder standard across all measure tables
- Document the exception in model documentation

## Display Folders (primary organization)
- Use Display Folders as the standard (UI-only, safe refactor)
- Use a stable folder taxonomy; examples:
  - Base
  - Time Intelligence
  - Variance
  - Ratios
  - Formatting
  - Tooltips
- Keep folder depth shallow (max 2 levels)

## Measure naming standard (mandatory)
- Use business language (Title Case)
- Keep names stable; avoid cryptic abbreviations
- Do not use technical prefixes/suffixes such as `m_`, `msr_`, `_calc`
- Use consistent suffix patterns for time/comparisons:
  - `Sales YTD`
  - `Sales MTD`
  - `Sales QTD`
  - `Sales PY`
  - `Sales YoY`
  - `Sales YoY %`
  - `Sales Rolling 12M`
- Ratio and percentage measures should end with `%` where appropriate:
  - `Margin %`
  - `Conversion %`
- Prefer model formatting for units/currency instead of embedding units in names

## Mini dictionary (recommended measure names)
Use these as reusable naming templates. Replace `<Metric>` with business metric names such as `Sales`, `Volume`, `Gross Margin`.

- Base and totals:
  - `<Metric>`
  - `Total <Metric>`
  - `<Metric> per Unit`
  - `<Metric> per Customer`
- Time intelligence:
  - `<Metric> MTD`
  - `<Metric> QTD`
  - `<Metric> YTD`
  - `<Metric> PY`
  - `<Metric> PY YTD`
  - `<Metric> Rolling 3M`
  - `<Metric> Rolling 12M`
- Variance and growth:
  - `<Metric> YoY`
  - `<Metric> YoY %`
  - `<Metric> vs Target`
  - `<Metric> vs Target %`
  - `<Metric> vs Budget`
  - `<Metric> vs Budget %`
  - `<Metric> vs Plan`
  - `<Metric> vs Plan %`
- Ratios and quality:
  - `<Metric> %`
  - `<Metric> Share %`
  - `<Metric> Mix %`
  - `<Metric> Rate %`
  - `<Metric> Index`
- Averages and counts:
  - `Average <Metric>`
  - `Distinct <Entity> Count`
  - `<Entity> Count`

## Dependency pattern (for maintainability)
- Create base measures first (single-responsibility aggregations)
- Build derived measures on top of base measures
- Reuse shared measures instead of repeating business logic in many places

## DAX style baseline
- Use `VAR ... RETURN` for non-trivial logic
- Keep filter logic explicit and readable
- Prefer `DIVIDE()` over `/` when denominator can be zero

## Measure metadata
Fill Description for important measures:
- business definition (what it calculates)
- filters/assumptions
- unit (currency, percent, etc.)
- grain and exclusions

## Field Parameters
- Use Field Parameters for user-driven switching of measures/dimensions
- Store Field Parameter tables in 30_Support_UI and name them with `_UI`
- For Q&A/Copilot scenarios, add explicit fallback measures where dynamic parameter logic may be ambiguous
