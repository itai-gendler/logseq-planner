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
- text: Shift Task dates by the difference between the grabbed day and the target day.
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

# Drag a linked task to another Calendar day

## Trigger

A linked task's chip is dragged onto another day in the Calendar.

## Outcome

The day it was picked up by lands on the target day; its Deadline and Scheduled move by the same number of days, each keeping its time.

## Edge cases

- Day moves do not need Edit dates.
