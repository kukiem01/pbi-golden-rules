# 02) Semantic Model — Design, Relationships, Visibility

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

## Naming in Fields pane
- Loaded analytical tables
  - Business names (Title Case with spaces)
- Disconnected/support tables (Group 30)
  - Must follow the `_UI` standard (see file 04)

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
