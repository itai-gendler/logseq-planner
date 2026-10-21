---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Expand nested node
  kind: actor
  entities:
  - entity: node
    effect: reads
    facts:
    - Title
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Planner state sets Collapsed parents to exclude the selected parent.
  kind: product
  entities:
  - entity: planner-state
    effect: changes
    facts:
    - Collapsed parents
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

# Unfold a nested parent

## Trigger

The user unfolds a folded nested parent.

## Outcome

Its child nodes are listed under it again.
