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
