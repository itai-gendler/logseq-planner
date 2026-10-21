---
kind: validation
routes:
  main: Planner in Logseq
steps:
- text: Submit the proposed name
  entities: []
  kind: actor
  contexts:
    main:
      place: planner::planning-view
  actor: planner-user
- text: Show the name error in Planner state
  entities:
  - entity: planner-state
    effect: changes
    facts:
    - Error
  kind: product
  contexts:
    main:
      place: planner::planning-view
  actor: planner-user
references:
- kind: code
  role: implementation
  target: src/storage.ts#createViewStore
- kind: code
  role: implementation
  target: src/ui/workspace.ts#save
- kind: doc
  role: intent
  target: docs/guide.md
---

# Reject an empty normalized name

## Trigger

The proposed name contains no content after name normalization.

## Outcome

The name must be corrected; no saved configuration is created.
