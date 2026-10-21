---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Choose the Matrix
  kind: actor
  entities: []
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Present nodes in Quadrants or Every value using both chosen axes; list missing-axis cards in Unplaced.
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
  target: src/core/matrix.ts
---

# Read the Matrix

## Trigger

The user opens the Matrix.

## Outcome

Each node is placed by its values on the two axes, in four quadrants or a row and column per value, and nodes missing an axis value are listed under Unplaced.

## Edge cases

- Hidden values remove cards from the grid and count them separately from Unplaced.
- Done cards are hidden and counted unless Show done is enabled.
- Cards sort by due date then title; Unplaced is newest first.
