---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Move the Node span
  kind: actor
  entities:
  - entity: node
    effect: reads
    facts:
    - Dates
    - Span
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Shift and confirm the Node dates
  kind: product
  entities:
  - entity: node
    effect: changes
    facts:
    - Dates
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
references:
- kind: code
  role: implementation
  target: src/ui/view-area.ts#dateMoveOf
- kind: code
  role: implementation
  target: src/core/when.ts#whenMove
- kind: code
  role: implementation
  target: src/core/date-edit.ts#writeDates
- kind: code
  role: implementation
  target: src/ui/workspace.ts#moveDate
- kind: doc
  role: intent
  target: docs/guide.md
---

# Move an existing editable span

## Trigger

Edit dates is enabled and the user moves an eligible Timeline or Calendar time-grid node.

## Outcome

The node’s own dates move together; derived spans and linked-task markers are unchanged.

## Edge cases

- Timeline Day and Calendar time-grid moves use quarter hours; other Timeline zooms use days.
- Calendar time-grid moves remain inside the shown day and range.
- Canceling before completion leaves graph dates unchanged.
