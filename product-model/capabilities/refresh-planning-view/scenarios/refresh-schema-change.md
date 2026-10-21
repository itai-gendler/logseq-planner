---
kind: edge
routes:
  main: Planner in Logseq
steps:
- text: The selected schema changes
  kind: condition
  entities: []
  unattended: true
  contexts:
    main:
      place: planner::planning-view
- text: Reconcile Tag and Property definitions
  kind: product
  entities:
  - entity: tag
    effect: reads
    facts:
    - Title
    - Properties
  - entity: property
    effect: reads
    facts:
    - Title
    - Type
    - Closed values
  contexts:
    main:
      place: planner::planning-view
- text: Replace incompatible Planner state settings and display the explanation
  kind: product
  entities:
  - entity: planner-state
    effect: changes
    facts:
    - Selected tags
    - Date mappings
    - Depends on
    - Done values
    - Filters
    - View kind
    - Timeline settings
    - Calendar settings
    - Agenda settings
    - Kanban settings
    - Matrix settings
    - Saved view
    - Error
    - Displayed data
  contexts:
    main:
      place: planner::planning-view
references:
- kind: code
  role: implementation
  target: src/ui/changes.ts#createChanges
- kind: code
  role: implementation
  target: src/ui/workspace.ts#reload
- kind: code
  role: implementation
  target: src/ui/block.ts#createBlocks
- kind: doc
  role: intent
  target: docs/guide.md
---

# Recover when selected schema disappears

## Trigger

A graph refresh finds deleted selected tags or properties.

## Outcome

Remaining tags are retained; if none remain or required settings are invalid, the default view and an error are shown.

## Edge cases

- Newly available properties fill previously unmapped defaults.
- A removed dependency property means None for that interpretation.
