---
kind: validation
routes:
  main: Planner in Logseq
steps:
- text: Read the available destinations for the Node
  entities:
  - entity: node
    effect: reads
    facts:
    - Dates
    - Span
  kind: actor
  contexts:
    main:
      place: planner::planning-view
  actor: planner-user
- text: Keep the Node dates while presenting only writable destinations
  entities:
  - entity: node
    effect: reads
    facts:
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

# Explain a When target without a writable day

## Trigger

The desired When target is Overdue or Later.

## Outcome

The current graph values remain unchanged; these periods are not move destinations.
