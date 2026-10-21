---
kind: alternate
routes:
  main: Planner in Logseq
steps:
- text: Choose the Node’s current destination
  entities:
  - entity: node
    effect: reads
    facts:
    - Choices
    - Dates
  kind: actor
  contexts:
    main:
      place: planner::planning-view
  actor: planner-user
- text: Retain the Node values
  entities:
  - entity: node
    effect: reads
    facts:
    - Choices
    - Dates
  kind: product
  contexts:
    main:
      place: planner::planning-view
  actor: planner-user
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

# Keep an existing value within the target band

## Trigger

The card is already in the selected Kanban cell or Matrix band.

## Outcome

No writes are made; a Matrix card retains its particular value inside the band.
