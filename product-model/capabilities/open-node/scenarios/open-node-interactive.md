---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Open the Node or Task
  kind: actor
  entities:
  - entity: node
    effect: reads
    facts:
    - Title
  - entity: task
    effect: reads
    facts:
    - Title
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Ask Logseq to open the selected Node or Task
  kind: product
  entities:
  - entity: node
    effect: reads
    facts:
    - Title
  - entity: task
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
  target: src/app.ts#nodeOpener
- kind: doc
  role: intent
  target: docs/guide.md
---

# Open an item from Planner

## Trigger

The user clicks a node or linked task in Planner, or Shift-clicks it for Logseq's sidebar.

## Outcome

Logseq opens the selected page or block.

## Decision points

### Destination

Where does the item open?

- Main page in Workspace → open the item and hide Planner.
- Main page while docked → open the item and keep Planner beside the page.
- Host sidebar → open the item and keep Planner visible.
