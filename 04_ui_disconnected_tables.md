# 04) Disconnected / Support Tables - 30_Support_UI

## Goal
- Disconnected tables are clearly identifiable
- Easy to find in the Fields pane and DAX autocomplete
- Naming scales with new tables regardless of origin or page usage

## One naming standard (mandatory)
All disconnected/support tables in 30_Support_UI must be named:

`_UI <Short User Name> [v2] [(Page)]`

## What each part means
- `_UI`
  - Marks the table as disconnected/support
  - Enables quick filtering/autocomplete in DAX by typing `_UI`
  - Tends to sort lower than letter-starting tables in Fields pane
- `<Short User Name>`
  - Concise, user-facing name describing what the selector controls
  - Prefer short nouns + common abbreviations (YTD, MAT, KPI)
- `[v2] / [v3]`
  - Only when multiple variants exist for the same selector
- `[(Page)]`
  - Only if the table is strictly page-only
  - If it can be reused, omit the page suffix

## Examples (good)
- `_UI Time (YTD/MAT)`
- `_UI Promo Mode`
- `_UI Seg Order v2`
- `_UI G2N Tooltip (Gross to Net)` *(page-only)*

## Examples (avoid)
- `PageName ...` *(pages change)*
- `UI_Portfolio_Cat1` *(technical, unclear in Fields pane)*
- mixed separators: `_`, `-`, `|` *(inconsistent scanning/searching)*

## Implementation notes
- If the table is used only to drive visuals and not meant for self-service:
  - consider hiding it in Fields pane (but keep the `_UI` prefix)
- Prefer stable keys:
  - include Index/Sort columns where needed
  - set “Do not summarize” for ID-like columns
