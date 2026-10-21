---
kind: edge
routes:
  main: Planner in Logseq
steps:
- text: Move the Node card to another When period in another choice swimlane
  kind: actor
  entities:
  - entity: node
    effect: reads
    facts:
    - Choices
    - Dates
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Write the Node due date for the target period first and read it back
  kind: product
  entities:
  - entity: node
    effect: changes
    facts:
    - Dates
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: The Node swimlane value fails to write or reads back differently
  kind: condition
  entities:
  - entity: node
    effect: reads
    facts:
    - Choices
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Put the Node earlier dates back and read them back
  kind: product
  entities:
  - entity: node
    effect: changes
    facts:
    - Dates
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Show in Planner state whether the dates were put back, and reload what the graph holds
  kind: product
  entities:
  - entity: planner-state
    effect: changes
    facts:
    - Error
    - Displayed data
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
references:
- kind: code
  role: implementation
  target: src/core/write.ts#writeInOrder
- kind: code
  role: implementation
  target: src/ui/workspace.ts#moveWhen
- kind: code
  role: implementation
  target: src/core/kanban.ts#moveDescriptor
- kind: code
  role: implementation
  target: src/core/matrix.ts#matrixMove
- kind: doc
  role: intent
  target: docs/guide.md
---

# Recover a partially written card move

## Trigger

A card moved by When into another swimlane gets its new date, but the swimlane write that follows fails.

## Outcome

The earlier dates are put back, the error says the card has not moved or that putting the date back failed too, and the board shows what the graph holds.

## Edge cases

- A move that changes a column and a choice swimlane writes the column first and puts it back the same way when the swimlane fails.
- A write whose read-back differs counts as failed, even when Logseq reported success.
