---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Move the Node to the target
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
- text: Set the Node End, otherwise Start, to the selected day; a new DateTime starts at midnight.
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

# Give an undated node a date

## Trigger

A node without dates of its own is dropped on a day from the No date tray or bucket.

## Outcome

The node gets its own End on that day, else its own Start, and appears in the dated views; a new DateTime starts at 00:00.

## Edge cases

- The node's tag must map a Start or End date in this view.
