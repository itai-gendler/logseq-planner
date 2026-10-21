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
- text: Write mapped dates first, then changed choice values, and confirm the graph.
  kind: product
  entities:
  - entity: node
    effect: changes
    facts:
    - Dates
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

# Move a card by When

## Trigger

A card is moved to a dated When period or band.

## Outcome

Its due date becomes the target’s last writable day and any changed choice axis or swimlane is stored.

## Edge cases

- A card already due within the target period keeps its dates.
- A node with Start and End keeps its length; one without dates of its own gets an End, else a Start.
