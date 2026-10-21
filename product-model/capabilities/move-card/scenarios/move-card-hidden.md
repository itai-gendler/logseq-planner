---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Move the Node card
  kind: actor
  entities:
  - entity: node
    effect: reads
    facts:
    - Title
    - Choices
    - Dates
    - Span
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Write and confirm the chosen value even when its column is hidden.
  kind: product
  entities:
  - entity: node
    effect: changes
    facts:
    - Choices
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
references:
- kind: code
  role: implementation
  target: src/core/kanban.ts#moveDescriptor
- kind: code
  role: implementation
  target: src/core/matrix.ts#matrixMove
- kind: code
  role: implementation
  target: src/ui/workspace.ts#move
- kind: code
  role: implementation
  target: src/ui/workspace.ts#moveWhen
- kind: doc
  role: intent
  target: docs/guide.md
---

# Move a card to a hidden column

## Trigger

The card's Move menu selects a column hidden from the board.

## Outcome

The value is written and read back, and the card leaves the visible board.
