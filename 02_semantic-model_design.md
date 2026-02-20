# 02) Semantic Model - Design, Relationships, Visibility

## Goal
- Self-service usability
- High performance
- Low ambiguity for users and AI

## Model design (default)
- Prefer **star schema**
  - Dimensions filter facts
  - Facts store events/transactions
- Relationships
  - Single-direction filtering by default
  - Bi-directional only when necessary and understood
  - Avoid many-to-many when possible; prefer bridge patterns

## Relationship quality checks (mandatory)
- Dimension keys should be unique and non-null
- Prefer `1:*` relationships from dimension to fact
- Avoid ambiguous filter paths between the same tables

## Date table and time intelligence
- Use one conformed Date table for the model (or a documented role-playing pattern)
- Mark the Date table as a Date table/Calendar and keep date range contiguous
- Disable Auto date/time for enterprise/shared models (use explicit Date table logic)
- Connect Date to facts with single-direction relationships by default
- For multiple date roles:
  - use inactive relationships + `USERELATIONSHIP()`, or
  - use role-playing Date dimensions when required by UX/performance

## Naming in Fields pane
- Loaded analytical tables
  - Business names (Title Case with spaces)
- Disconnected/support tables (Group 30)
  - Should follow the `_UI` standard (see file 04)
  - If not possible, document the exception

## Column visibility (clean field list)
- Hide by default:
  - surrogate keys / relationship keys
  - technical IDs not needed for reporting
  - helper columns used only by measures
- Show only:
  - user-facing attributes and hierarchies
  - fields intended for self-service

## Units and formatting (baseline)
- Ensure measures carry the formatting (currency/percent/decimal)
- Avoid formatting numbers as text in columns unless necessary
