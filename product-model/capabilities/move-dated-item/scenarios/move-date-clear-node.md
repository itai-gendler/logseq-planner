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
- text: Remove the Node mapped dates.
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

# Drop a node on No date

## Trigger

A dated node is dropped on the Calendar's No date tray or moved to No date.

## Outcome

Its own mapped dates are removed; when it has dated linked tasks, it shows again with the span they derive.

## Edge cases

- Day moves do not need Edit dates.
