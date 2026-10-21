---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Collapse nested node
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
- text: Planner state sets Collapsed parents to include the selected parent.
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

# Fold a nested parent

## Trigger

The user folds a nested parent in the Timeline.

## Outcome

The parent's row stays with its progress, and its child nodes are hidden until it is unfolded.
