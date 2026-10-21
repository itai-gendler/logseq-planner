---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Open the Saved view
  kind: actor
  entities:
  - entity: saved-view
    effect: reads
    facts:
    - Name
    - Settings
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Load the Saved view into Planner state
  kind: product
  entities:
  - entity: saved-view
    effect: reads
    facts:
    - Settings
  - entity: planner-state
    effect: changes
    facts:
    - Selected tags
    - Include child tags
    - Date mappings
    - Depends on
    - Done values
    - Filters
    - Find
    - Added
    - View kind
    - Timeline settings
    - Calendar settings
    - Agenda settings
    - Kanban settings
    - Matrix settings
    - Saved view
    - Displayed data
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
references:
- kind: code
  role: implementation
  target: src/ui/workspace.ts#openSaved
- kind: code
  role: implementation
  target: src/app.ts#registerApp
- kind: doc
  role: intent
  target: docs/guide.md
---

# Open a saved view from the list

## Trigger

The user chooses a readable saved view under Saved views.

## Outcome

Planner shows that saved configuration and marks it as the open saved view, keeping the period being looked at.

## Edge cases

- Missing selected tags are dropped while at least one remains.
- Settings that cannot be applied produce an explanatory error.
- Old single-tag configurations are read as one selected tag with its original mappings.
