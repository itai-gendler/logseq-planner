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
- text: Remove the relevant values and confirm their absence.
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

# Move a card to No value

## Trigger

The user moves a card to No property or Matrix Unplaced.

## Outcome

The selected values are removed; Matrix Unplaced clears both axis values.

## Edge cases

- A When column or axis removes the node's own dates instead.
