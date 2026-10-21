---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Move the Task to the target
  kind: actor
  entities:
  - entity: task
    effect: reads
    facts:
    - Scheduled
    - Deadline
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Remove the Task Scheduled and Deadline values.
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Scheduled
    - Deadline
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

# Drop a linked task on No date

## Trigger

A dated linked task is dropped on the Calendar's No date tray.

## Outcome

Its Scheduled and Deadline are removed, and the node it belongs to no longer takes a span from those dates.

## Edge cases

- Day moves do not need Edit dates.
