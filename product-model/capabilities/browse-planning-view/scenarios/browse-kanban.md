---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Choose the Kanban
  kind: actor
  entities: []
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Present nodes under the chosen choice values or When periods, with optional choice or Tag swimlanes.
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
  - entity: tag
    effect: reads
    facts:
    - Title
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
references:
- kind: code
  role: implementation
  target: src/core/kanban.ts
---

# Read the Kanban board

## Trigger

The user opens the Kanban.

## Outcome

Each node is a card in the column of its value, or of its When period, with optional swimlanes by another choice property or by tag.

## Edge cases

- Counts retain total matching cards when only the first 50 per cell are shown; Show more extends the list.
- A choice board shows done cards; a When board hides and counts them.
- When Overdue and No date lists are newest first regardless of Sort.
