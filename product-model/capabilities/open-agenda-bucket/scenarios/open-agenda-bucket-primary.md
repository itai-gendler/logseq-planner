---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Open Agenda bucket
  kind: actor
  entities: []
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Planner state sets Open Agenda buckets to include the selected bucket.
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

# Unfold an Agenda bucket

## Trigger

The user opens the folded Later, No date or Earlier bucket.

## Outcome

The bucket lists its entries, and it stays open while the view refreshes after graph changes.
