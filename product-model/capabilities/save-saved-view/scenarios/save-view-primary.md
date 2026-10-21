---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Enter a name for the current configuration
  kind: actor
  entities:
  - entity: planner-state
    effect: reads
    facts:
    - Selected tags
    - Date mappings
    - View kind
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Create the Saved view from the current settings
  kind: product
  entities:
  - entity: saved-view
    effect: creates
    facts:
    - Name
    - Settings
    - Readability
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Select the new Saved view in Planner state
  kind: product
  entities:
  - entity: saved-view
    effect: reads
    facts:
    - Name
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
  target: src/ui/workspace.ts#save
- kind: doc
  role: intent
  target: docs/guide.md
---

# Save a planning configuration

## Trigger

The user enters a name and saves the current view.

## Outcome

A new saved view is stored and read back, and the current view is associated with it.

## Edge cases

- The views page and its hidden config property are created when needed.
- Names are normalized before saving; a name empty after normalization is rejected.
- The current period, expanded rows and device preferences are not included.
