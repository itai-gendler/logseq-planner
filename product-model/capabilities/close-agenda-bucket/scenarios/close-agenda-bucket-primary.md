---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Close Agenda bucket
  kind: actor
  entities: []
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Planner state sets Open Agenda buckets to exclude the selected bucket.
  kind: product
  entities:
  - entity: planner-state
    effect: changes
    facts:
    - Open Agenda buckets
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
references:
- kind: code
  role: implementation
  target: src/ui/workspace.ts#createWorkspace
- kind: doc
  role: intent
  target: docs/guide.md
---

# Fold an Agenda bucket

## Trigger

The user folds an open Later, No date or Earlier bucket.

## Outcome

The bucket's entries are no longer listed; the other buckets and the graph are unchanged.
