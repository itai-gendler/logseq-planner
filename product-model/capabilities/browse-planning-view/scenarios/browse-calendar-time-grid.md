---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Choose the Calendar in Day, 3 days or Week
  kind: actor
  entities: []
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Present the selected Day, 3 days or Week with timed nodes and both Scheduled and Deadline occurrences of
    linked tasks.
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

# Read a Calendar time grid

## Trigger

The user opens the Calendar in Day, 3 days or Week.

## Outcome

A 24-hour grid places timed items by their minutes and lists the rest in the all-day row, with both the Scheduled and the Deadline of linked tasks.

## Edge cases

- A same-day mapped DateTime span is timed; derived, date-only and multi-day spans remain all-day.
- A point or task occurrence represents a 30-minute display block without changing its stored duration.
- The 3 days range is yesterday, the anchor day and tomorrow.
