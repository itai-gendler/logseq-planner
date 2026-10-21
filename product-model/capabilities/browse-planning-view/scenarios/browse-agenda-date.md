---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Choose the Agenda grouped by date
  kind: actor
  entities: []
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Present Overdue, Today and the next 14 days, then Later, No date and Earlier when nonempty.
  kind: product
  entities:
  - entity: node
    effect: reads
    facts:
    - Title
    - Tags
    - Dates
    - Choices
    - Fields
    - References
    - Created day
    - Span
    - Progress
  - entity: task
    effect: reads
    facts:
    - Title
    - Scheduled
    - Deadline
    - Status
    - References
    - Created day
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
references:
- kind: code
  role: implementation
  target: src/core/agenda.ts
---

# Read the Agenda by date

## Trigger

The user opens the Agenda grouped by date.

## Outcome

Overdue work, today and each of the next 14 days are listed with their nodes and linked tasks, followed by the folded Later, No date and Earlier buckets when they hold anything.

## Edge cases

- A task referenced by several nodes appears once by date.
- A derived-only parent is omitted as a separate date entry, leaving its tasks.
- Show done includes recent completed entries and undated ones, but not completed entries in Later.
