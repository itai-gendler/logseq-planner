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
- text: Set the Task Deadline to the target day at midnight.
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

# Give an undated linked task a date

## Trigger

A linked task without Scheduled or Deadline is dropped on a day.

## Outcome

The task gets a Deadline on that day and appears in the dated views.
