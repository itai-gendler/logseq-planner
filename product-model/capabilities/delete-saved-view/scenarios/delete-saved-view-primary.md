---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Confirm deletion of the Saved view
  kind: actor
  entities:
  - entity: saved-view
    effect: reads
    facts:
    - Name
    - Readability
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Remove the Saved view
  kind: product
  entities:
  - entity: saved-view
    effect: removes
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Clear the deleted configuration association from Planner state
  kind: product
  entities:
  - entity: planner-state
    effect: changes
    facts:
    - Saved view
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
  target: src/ui/workspace.ts#viewsWrite
- kind: doc
  role: intent
  target: docs/guide.md
---

# Confirm deletion of a saved configuration

## Trigger

The user selects a saved view for deletion.

## Outcome

Its block is removed and absence is checked; deleting the active saved view detaches the current settings from it.

## Edge cases

- Cancel leaves the configuration unchanged.
- The same deletion flow accepts an unreadable configuration.
- If the block still exists after removal, an error is shown and the local list entry returns.
