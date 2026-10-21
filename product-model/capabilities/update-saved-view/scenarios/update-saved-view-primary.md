---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Update the active Saved view
  kind: actor
  entities:
  - entity: saved-view
    effect: reads
    facts:
    - Name
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Store the Saved view settings
  kind: product
  entities:
  - entity: saved-view
    effect: changes
    facts:
    - Settings
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

# Replace a saved configuration

## Trigger

A saved view is active and its settings have changed.

## Outcome

The same saved view holds the replacement settings after read-back confirmation.

## Edge cases

- A failed write shows its reason and restores the prior local list entry.
- A deleted saved view cannot be updated as if it still exists.
