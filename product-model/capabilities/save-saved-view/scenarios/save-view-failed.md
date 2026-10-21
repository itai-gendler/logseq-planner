---
kind: edge
routes:
  main: Planner in Logseq
steps:
- text: Save the current settings
  kind: actor
  entities: []
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Record the save failure in Planner state
  kind: product
  entities:
  - entity: planner-state
    effect: changes
    facts:
    - Error
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
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

# Recover from an unconfirmed save

## Trigger

A new configuration cannot be confirmed in the graph.

## Outcome

The save error is shown and cleanup of the newly appended block is attempted; a cleanup failure is also reported.

## Edge cases

- A views page in Recycle produces guidance to restore or remove it in Logseq before retrying.
- No saved configuration is reported as successfully created without read-back confirmation.
