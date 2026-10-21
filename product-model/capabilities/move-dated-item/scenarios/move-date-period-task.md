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
- text: Set the Task Deadline to the target day and shift Scheduled equally; Scheduled alone moves when no Deadline
    exists.
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

# Reschedule a linked task in the Agenda

## Trigger

A linked task's Agenda entry is dragged onto a day heading or offered period.

## Outcome

The task is due by that day: its Deadline lands on it and its Scheduled moves by the same days; a task with only Scheduled moves that date.

## Edge cases

- A task already due within the target keeps its dates.
