# 04) Disconnected / Support Tables - 30_Support_UI

## Goal
- Disconnected tables are clearly identifiable
- Easy to find in the Fields pane and DAX autocomplete
- Naming scales with new tables regardless of origin or page usage

## One naming standard (mandatory)
All disconnected/support tables in 30_Support_UI must be named:

`_UI <Short User Name> [(Set/Clarifier)] [v2]`

## What each part means
- `_UI`
  - Marks the table as disconnected/support
  - Enables quick filtering/autocomplete in DAX by typing `_UI`
  - Tends to sort lower than letter-starting tables in Fields pane
- `<Short User Name>`
  - Concise, user-facing name describing what the selector controls
  - Prefer short nouns + common abbreviations (YTD, MAT, KPI)
- `[(Set/Clarifier)]`
  - Optional clarification of the value set or role (not a page name)
  - Use for compact, user-friendly disambiguation (keep it short)
  - Examples: `(YTD/MAT)`, `(CY/PY)`, `(Tooltip)`, `(Chart 1)`, `(Icons)`
- `[v2] / [v3]`
  - Only when multiple variants exist for the same selector
  - Use `v2` instead of suffixes like `Cat1/Cat2`, `Order2`, etc.

## Page-only usage
- Do not encode report page scope in the table name
- If a table is strictly page-only, capture scope in one of these places:
  - Table **Description** (recommended)
  - Query Group structure (foldering)
  - Documentation
- Avoid using `@` in table names (it can work, but is less consistent and may hinder autocomplete patterns)

## Examples (good)
- `_UI Time (YTD/MAT)`
- `_UI Year (CY/PY)`
- `_UI Promo Mode`
- `_UI Seg Order v2`
- `_UI G2N Tooltip` *(page-only scope stored in Description)*

## Examples (avoid)
- `PageName ...` *(pages change)*
- `UI_Portfolio_Cat1` *(technical, unclear in Fields pane)*
- mixed separators: `_`, `-`, `|` *(inconsistent scanning/searching)*
- embedding scope as a page name in parentheses *(parentheses reserved for set/clarifier)*

## Implementation notes
- If the table is used only to drive visuals and not meant for self-service:
  - consider hiding it in the Fields pane (but keep the `_UI` prefix)
- Prefer stable keys:
  - include Index/Sort columns where needed
  - set “Do not summarize” for ID-like columns
- Keep names short:
  - If more disambiguation is required, prefer Description over longer names
