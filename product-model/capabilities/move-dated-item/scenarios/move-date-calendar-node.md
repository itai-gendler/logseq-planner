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
- text: Shift Node dates by the difference between the grabbed day and the target day.
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

# Drag a node to another Calendar day

## Trigger

A node's band or chip is dragged onto another day in the Calendar.

## Outcome

The day it was picked up by lands on the target day and its other date moves with it, so a span keeps its length and a DateTime its time.

## Edge cases

- The node's tag must map a Start or End date in this view.
- Day moves do not need Edit dates.
