---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Expand task rows
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
- text: Planner state sets Expanded task rows to include the selected node.
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

# Unfold a node's task rows

## Trigger

The user expands a node that has linked tasks.

## Outcome

Each linked task gets a row with its Scheduled and Deadline markers, and the rows stay open while the view refreshes.
