---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Collapse task rows
  kind: actor
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Planner state sets Expanded task rows to exclude the selected node.
  kind: product
  entities:
  - entity: planner-state
    effect: changes
    facts:
    - Expanded task rows
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
  target: src/ui/workspace.ts#timeline
- kind: doc
  role: intent
  target: docs/guide.md
---

# Fold a node's task rows

## Trigger

The user folds a node whose linked tasks are shown as rows.

## Outcome

The node keeps its bar and progress; its task rows are hidden.
