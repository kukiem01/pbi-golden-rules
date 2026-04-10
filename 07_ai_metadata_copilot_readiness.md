# 07) AI Metadata And Copilot Readiness

## Scope
- Profiles: `Universal Baseline`, `Enterprise / Shared Model`, and selected `Situational Pattern` usage.
- This document is Copilot-first. Legacy Q&A guidance lives in `appendix_legacy_qna.md`.

## Goal
- Reduce ambiguity for natural-language experiences and improve discoverability, trust, and reuse.

## Core Metadata Hygiene
- MUST: Use human-readable names for tables, columns, and measures.
- MUST: Distinguish similarly named fields across tables when ambiguity would hurt interpretation.
- MUST: Keep relationships correct, complete, and intentional.
- MUST: Use correct data types.
- SHOULD: Set Data Category for geography and similar fields.
- MUST: Set IDs and key-like fields to `Do not summarize`.

## Descriptions
- SHOULD: Add descriptions for important tables, columns, and measures in published or shared models.
- MUST: Add descriptions for business-critical or non-obvious measures.
- SHOULD: Add descriptions for fields whose meaning is not obvious from the name alone.
- MAY: Add richer AI-oriented descriptions or instructions when the organization actively uses Copilot features.

## Curation
- MUST: Hide noisy technical fields.
- MUST: Hide purely technical `_UI` columns from end users unless visibility is intentional.
- SHOULD: Keep the visible field list focused on business concepts, intentional selectors, and reusable metrics.

## Semantic Readiness For AI
- SHOULD: Prefer explicit, well-named measures for critical business questions.
- SHOULD: Reduce unnecessary ambiguity in model naming and structure before adding AI-specific polish.
- MUST: Provide a clear fallback path for critical questions when disconnected selectors or Field Parameters drive the UX.
- AVOID: Depending on dynamic selector logic alone for the most important semantic paths.

## Platform Direction
- MUST: Treat this document as the primary guidance for AI readiness in the repo.
- SHOULD: Recheck preview-sensitive Copilot features against current Microsoft guidance before adopting deeper AI-specific instructions.
- AVOID: Building new long-term standards around legacy Q&A behavior.
