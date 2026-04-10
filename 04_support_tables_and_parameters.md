# 04) Support Tables And Parameters

## Scope
- Profiles: `Enterprise / Shared Model` and `Situational Pattern`
- Use this document only when the model contains disconnected tables, support tables, or field parameters.

## Goal
- Make support objects predictable for modelers without polluting the user-facing semantic layer.

## Support Object Types
- `Technical hidden support table`
  - Exists to drive logic, sorting, visuals, or parameters.
  - Hidden from report authors unless visibility is intentionally required.
- `Visible user selector`
  - Exposed intentionally because users or report authors need to interact with it.

## Naming Standard
- MUST: Name disconnected or support tables with the `_UI` pattern:
  - `_UI <Short Name> [(Clarifier)]`
- SHOULD: Keep `<Short Name>` concise and business-readable.
- MAY: Add `v2` or `v3` only as a temporary transition marker when two live variants must coexist.
- AVOID: Encoding report page names in the table name.
- AVOID: Mixed separators such as `_`, `-`, and `|` in the same naming system.
- SHOULD: Put extra scope in the table description instead of stretching the table name.

## Visibility
- MUST: Hide technical-only `_UI` tables and columns from the Fields pane.
- MAY: Expose a `_UI` table when it is an intentional user selector.
- MUST: Hide purely technical helper columns even when the table itself is visible.
- SHOULD: Distinguish clearly between support objects for modelers and fields intended for self-service authors.

## Implementation Notes
- SHOULD: Keep stable sort and key columns where the selector depends on ordering.
- MUST: Set ID-like columns to `Do not summarize`.
- SHOULD: Keep names short and rely on descriptions for additional context.

## Field Parameters
- MAY: Use Field Parameters for controlled UX switching.
- SHOULD: Use names such as `_UI Metric Selector` or `_UI Axis Selector`.
- MUST: Treat Field Parameters as a situational pattern, not as a universal standard.
- MUST: Provide a fallback measure path or equivalent explanation in AI-facing or self-service-heavy models.
- AVOID: Relying only on a Field Parameter for critical business semantics.
