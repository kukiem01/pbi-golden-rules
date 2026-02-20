# 06) AI / Q&A / Copilot - Metadata Hygiene

## Goal
- Reduce ambiguity in natural language queries
- Improve discoverability and correctness

## Core rules
- Add Description to:
  - tables
  - columns
  - measures
- Add Synonyms for business terms when useful
- Ensure relationships are correct and complete

## Data typing and categories
- Use correct data types (Date as Date, numbers numeric)
- Set Data Category for geography and similar fields
- Default summarization:
  - IDs and keys should be “Do not summarize”

## Curation
- Hide noisy technical fields
- Keep naming consistent:
  - facts/dims: business names
  - support/disconnected: `_UI` standard

## Q&A / Copilot practical constraints
- Prefer explicit, well-named measures for natural language reliability
- Field Parameters and dynamic selector logic can be less predictable in Q&A
- For critical business questions, provide explicit fallback measures and synonyms
- Hide purely technical `_UI` columns from end users when they do not add semantic value
