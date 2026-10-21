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
- text: Write the changed column first and then the changed lane; read both back.
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

# Move a card across a column and swimlane

## Trigger

A card changes its column and choice swimlane.

## Outcome

The card and graph agree on its new choice values.

## Edge cases

- A card that is still being written takes no other move until its write finishes.
- A move across Tag swimlanes is refused: a card keeps its tag.
