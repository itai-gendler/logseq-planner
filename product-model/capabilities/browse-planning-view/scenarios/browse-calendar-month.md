---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Choose the Calendar in Month
  kind: actor
  entities: []
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Present the whole weeks covering the month, multi-day spans, one-date items and linked task deadlines.
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
  target: src/core/calendar-layout.ts
---

# Read the Calendar month

## Trigger

The user opens the Calendar in Month.

## Outcome

The whole weeks covering the month show multi-day spans as bands and one-date items and linked task deadlines as chips; undated nodes wait in the No date tray.

## Edge cases

- Scheduled task dates are omitted in Month.
- Overflow opens the selected day’s Week view.
- Undated nodes are listed newest first in No date.
