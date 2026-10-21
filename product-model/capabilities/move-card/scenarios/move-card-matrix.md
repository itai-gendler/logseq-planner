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
- text: Write the changed axis values and read them back.
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

# Move a card between Matrix bands

## Trigger

A card is placed in a different Matrix cell.

## Outcome

Each changed choice axis receives the first value of its target band; unchanged-band values are preserved.

## Edge cases

- A card that stays in its band on an axis keeps its value on that axis.
