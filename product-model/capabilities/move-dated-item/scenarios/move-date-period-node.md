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
- text: Set the Node End to the last day of the target and shift Start equally; a single own date moves alone.
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

# Reschedule a node in the Agenda

## Trigger

A node's Agenda entry is dragged onto a day heading or offered period.

## Outcome

The node is due by that day: its End lands on it and its Start moves by the same days, keeping the length and local times; a node with one date moves that date.

## Edge cases

- A node already due within the target keeps its dates.
- The node's tag must map a Start or End date in this view.
